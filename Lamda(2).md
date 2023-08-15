	[[매]]
	(타입 매개변수, 타입 매개변수...) -> {
		실행문;
		실행문;
		...
		실행문;
	}
매개변수의  <font color = "FFDAB9">타입은 생략할 수 있음</font>
<br />
매개변수가 2개인 추상메소드 work()를 가지는 인터페이스 workable을 작성

		@FunctionalInterface
		public interface Workable() {
			void work(String name, String job)
		};

<br />
매개변수가 1개인 추상메소드 speak()를 가지는 인터페이스 speakable을 작성

	@FunctionalInterface
	public interface Speakable() {
		void speak(String content)
	};

<br />
함수형 인터페이스인 Workable, Speakable을 각각 매개변수로 갖는 메소드 action1(), action2()를 작성한다.

	public class Person {
		public void action1(Workable workable) {
			workable.work("홍길동", "프로그래밍");
		}

		public void action2(Speakable speakable) {
			speakable.speak("반갑습니다.");
		}
	}

<br />
실행 클래스를 작성한다.

	public class LamdaExample {
		public static void main() {

			Person person = new Person();

	// 매개변수가 2개인 경우
	person.action1((name, job) -> {
		System.out.println(name + "이" + job + "을 합니다."); 
	});

	// 매개변수가 1개인 경우
	person.action2((content) -> {
		System.out.println("\"" + content + "\" + 라고 말합니다.")
	});
	}
	}

