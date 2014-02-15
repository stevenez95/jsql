This is a quite simple expression evaluator of additions and multiplications using JSqlParser. The ExpressionDeParser is used to traverse and interpret the parse tree.

    import java.util.Stack;
	import net.sf.jsqlparser.JSQLParserException;
	import net.sf.jsqlparser.expression.Expression;
	import net.sf.jsqlparser.expression.LongValue;
	import net.sf.jsqlparser.expression.operators.arithmetic.Addition;
	import net.sf.jsqlparser.expression.operators.arithmetic.Multiplication;
	import net.sf.jsqlparser.parser.CCJSqlParserUtil;
	import net.sf.jsqlparser.util.deparser.ExpressionDeParser;
	
	/**
	 *
	 * @author toben
	 */
	public class SimpleEvaluateExpr {
	    
	    public static void main( String[] args ) throws JSQLParserException {
		evaluate("4+5*6");
		evaluate("4*5+6");
		evaluate("4*(5+6)");
		evaluate("4*(5+6)*(2+3)");
	    }
	
	    static void evaluate(String expr) throws JSQLParserException {
		final Stack<Long> stack = new Stack<Long>();
		System.out.println("expr=" + expr);
		Expression parseExpression = CCJSqlParserUtil.parseExpression(expr);
		ExpressionDeParser deparser = new ExpressionDeParser() {
		    @Override
		    public void visit(Addition addition) {
			super.visit(addition); 
			
			long sum1 = stack.pop();
			long sum2 = stack.pop();
			
			stack.push(sum1 + sum2);
		    }
	
		    @Override
		    public void visit(Multiplication multiplication) {
			super.visit(multiplication); 
			
			long fac1 = stack.pop();
			long fac2 = stack.pop();
			
			stack.push(fac1 * fac2);
		    }
	
		    @Override
		    public void visit(LongValue longValue) {
			super.visit(longValue); 
			stack.push(longValue.getValue());
		    }
		};
		StringBuilder b = new StringBuilder();
		deparser.setBuffer(b);
		parseExpression.accept(deparser);
		
		System.out.println(expr + " = " + stack.pop() );
	    }
	}

And this is the result output:

    expr=4+5*6
	4+5*6 = 34
	expr=4*5+6
	4*5+6 = 26
	expr=4*(5+6)
	4*(5+6) = 44
	expr=4*(5+6)*(2+3)
	4*(5+6)*(2+3) = 220