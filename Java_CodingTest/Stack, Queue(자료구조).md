## 1. 올바른 괄호
```
	public String solution(String str) {
		String answer = "YES";
		Stack<Character> stack = new Stack<>();
		for (char x : str.toCharArray()) {
			if (x == '(')
				stack.push(x);
			else { //닫는 가로를 만나면
				if (stack.isEmpty()) //비어있으면NO 있으면 꺼내
					return "NO";
				stack.pop();
			}
		}
		if (!stack.isEmpty()) //여는가로가남아있으면
			return "NO";
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String str = kb.next();
		System.out.println(T.solution(str));
	}
}
```
## 2. 괄호문자제거
```
	public String solution(String str) {
		String answer = "";
		Stack<Character> stack = new Stack<>();
		for (char x : str.toCharArray()) {
			if (x == ')') {
				while (stack.pop() != '(') //pop은제일위에있는것을꺼낸다
					; //꺼내고여는가로가아니면참이니까while한다
			} else
				stack.push(x);
		}
		for (int i = 0; i < stack.size(); i++)
			answer += stack.get(i);
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String str = kb.next();
		System.out.println(T.solution(str));
	}
}
```
## 3. 크레인 인형뽑기(카카오)
```
	public int solution(int[][] board, int[] moves) {
		int answer = 0;
		Stack<Integer> stack = new Stack<>();
		for (int pos : moves) {
			for (int i = 0; i < board.length; i++) { // 행크기
				if (board[i][pos - 1] != 0) { // 인형이발견되면(0은=인형없음)
					int tmp = board[i][pos - 1]; // 인형번호
					board[i][pos - 1] = 0; // 인형가져왔으니빈칸으로
					if (!stack.isEmpty() && tmp == stack.peek()) { // peek-값만확인
						answer += 2;
						stack.pop(); // 상단1개빼기
					} else
						stack.push(tmp); // 다른인형이면그냥푸쉬
					break; // 인형을만났으면for문break
				}
			}
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int[][] board = new int[n][n];
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				board[i][j] = kb.nextInt();
			}
		}
		int m = kb.nextInt();
		int[] moves = new int[m];
		for (int i = 0; i < m; i++)
			moves[i] = kb.nextInt();
		System.out.println(T.solution(board, moves));
	}
}
```
## 4. 후위식 연산(postfix)
```
	public int solution(String str) {
		int answer = 0;
		Stack<Integer> stack = new Stack<>();
		for (char x : str.toCharArray()) {
			if (Character.isDigit(x)) {
				stack.push(x - 48);
			} else {
				int rt = stack.pop();
				int lt = stack.pop();
				if (x == '+')
					stack.push(lt + rt);
				else if (x == '-')
					stack.push(lt - rt);
				else if (x == '*')
					stack.push(lt * rt);
				else if (x == '/')
					stack.push(lt / rt);
			}
		}
		answer = stack.get(0);
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String str = kb.next();
		System.out.println(T.solution(str));
	}
}
```
## 5. 쇠막대기
```
	public int solution(String str) {
		int cnt = 0;
		Stack<Character> stack = new Stack<>();
		for (int i = 0; i < str.length(); i++) {
			if (str.charAt(i) == '(')
				stack.push('(');
			else {
				stack.pop();
				if (str.charAt(i - 1) == '(')
					cnt += stack.size();
				else
					cnt++;
			}
		}
		return cnt;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String str = kb.next();
		System.out.println(T.solution(str));
	}
}
```
## 6. 공주구하기
```
	public int solution(int n, int k) {
		int answer = 0;
		Queue<Integer> Q = new LinkedList<>();
		for (int i = 1; i <= n; i++)
			Q.offer(i); // i를전부넣는다
		while (!Q.isEmpty()) { // 비어있을때 참
			for (int i = 1; i < k; i++)
				Q.offer(Q.poll()); //poll은꺼내고리턴받음,뒤에다다시offer
			Q.poll();
			if (Q.size() == 1)
				answer = Q.poll(); //1개남으면답,Q가비었으면while문종료
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int k = kb.nextInt();
		System.out.println(T.solution(n, k));
	}
}
```
## 7. 교육과정설계
```
	public String solution(String need, String plan) {
		String answer = "YES";
		Queue<Character> Q = new LinkedList<>();
		for (char x : need.toCharArray())
			Q.offer(x); //Q에필수과목세팅
		for (char x : plan.toCharArray()) {
			if (Q.contains(x)) {
				if (x != Q.poll()) //맨앞쪽껄꺼냈더니필수과목이아니다
					return "NO";
			}
		}
		if (!Q.isEmpty())
			return "NO"; //필수과목이남아있어이수를안한상태
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String a = kb.next();
		String b = kb.next();
		System.out.println(T.solution(a, b));
	}
}
```
## 8. 응급실
```
class Person {
	int id;
	int priority;

	public Person(int id, int priority) {
		this.id = id;
		this.priority = priority;
	}
}

class Main {
	public int solution(int n, int m, int[] arr) {
		int answer = 0;
		Queue<Person> Q = new LinkedList<>();
		for (int i = 0; i < n; i++) {
			Q.offer(new Person(i, arr[i])); //객체생성(사람번호,위험도)
		}
		while (!Q.isEmpty()) {
			Person tmp = Q.poll(); //tmp라는환자를꺼낸다
			for (Person x : Q) {
				if (x.priority > tmp.priority) {
					Q.offer(tmp); //대기목록뒤에다가넘긴다
					tmp = null;
					break;
				}
			}
			if (tmp != null) {
				answer++;
				if (tmp.id == m)
					return answer;
			}
		}
		return answer;
	}

	public static void main(String[] args) throws IOException {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int m = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = kb.nextInt();
		}
		System.out.println(T.solution(n, m, arr));
	}
}
```
