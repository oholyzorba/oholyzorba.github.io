	( ) -> {
		실행문;
		실행문;
		}

람다식 : 데이터처리부에 제공되는 함수 역할을 하는 중괄호 블럭(매개변수를 가짐. 없는 경우도 있음)
람다식의 기본 형태 : (매개변수, ..., ...) -> { 처리내용 }

데이터처리부 : 람다식을 받아 매개변수에 데이터를 대입하고 중괄호 블럭을 실행시킴


<U>인터페이스를 실제 구현하는 <font color = "FFDAB9">익명 구현 객체</font> 를 <font color="00FF7F">람다식</font>으로 표현하려면
<font color="FFDAB9">인터페이스가 단 하나의 추상 메소드만</font> 가져야 함.</U> 이러한 인터페이스를 함수형 인터페이스(functional interface)라고 함.  => ==왜? 왜 하나의 추상메소드만 가져야하지? 이름이 다른 추상메소드들 여러 개 있어도 되잖아==

인터페이스가 함수형 인터페이스임을 보장하기위해서는 @FunctionalInterface 어노테이션을 붙이면 됨
(선택사항. compile과정에서 추상메소드가 하나인지 검사해주기 때문에 정확한 함수형 인터페이스를 작성할 수 있게 도와줌)

	@FunctionalInterface
	public interface Calculable() {
	void calculate(int x, int y);
	}

<br /> 1. 생성자를 이용하기
<font color="00FF7F">calculate()메소드의 실행블럭(처리내용) 내용을 한 가지로 밖에 못함</font>

	public class ConstructorExample extends Calculable {
		public static void main(String[] args) {
		
			new Calculable() {
			@Override
			public void calculate(int x, int y){ x+y }
			};
			
		};
	};


	

<br /> 2. 람다식을 이용하기
<font color="00FF7F">calculate()메소드의 처리내용을 여러가지로 할 수 있음 : 데이터처리의 다형성<br />
(x, y) -> { 처리내용1 };<br />
(x, y) -> { 처리내용2 };</font>


		
	public class LamdaExample extends Calculable {
		public static void main(String[] args) {
		
			action((x, y) -> { int result = x+y;
			System.out.println("result: " + result);
		});
			action((x, y) -> {int result = x-y;
			System.out.println("result: " + result)
		});
		
		public static void action(Calculable calculable) {
			int x = 10;
			int y = 4;

			calculable.calculate(x, y);
		}
	}

