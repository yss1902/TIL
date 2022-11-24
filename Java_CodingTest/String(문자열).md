## 1. 문자 찾기
```
	public int solution(String str, char t) {
		int answer = 0;
		str = str.toUpperCase();
		t = Character.toUpperCase(t);
		for (int i = 0; i < str.length(); i++) {
			if (str.charAt(i) == t)
				answer++;
		}

		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.next();
		char c = sc.next().charAt(0);

		System.out.print(T.solution(str, c));

	}

}
```
## 2. 대소문자 변환
```
	public String solution(String str) {
		String answer = "";
		for (char x : str.toCharArray()) {
			if (Character.isLowerCase(x))
				answer += Character.toUpperCase(x);
			else
				answer += Character.toLowerCase(x);
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.next();

		System.out.print(T.solution(str));

	}

}
```
## 3. 문장 속 단어
```
	public String solution(String str) {
		String answer = "";
		int m = Integer.MIN_VALUE;
		String[] s = str.split(" ");
		for (String x : s) { // 단어 하나하나가 대응된다. 배열이니 for each가 가능
			int len = x.length();
			if (len > m) {
				m = len;
				answer = x;
			}
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine(); // 단어가 아니라 한문장을 입력받으려면 nextLine

		System.out.print(T.solution(str));

	}

}
```
## 4. 단어 뒤집기
```
	public ArrayList<String> solution(int n, String[] str) {
		ArrayList<String> answer = new ArrayList<>();
		for (String x : str) {
			String tmp = new StringBuilder(x).reverse().toString();
			answer.add(tmp);

		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		String[] str = new String[n];
		for (int i = 0; i < n; i++) {
			str[i] = sc.next();
		}
		for (String x : T.solution(n, str)) {
			System.out.println(x);
		}

	}

}
```
## 5. 특정 문자 뒤집기
```
	public String solution(String str) {
		String answer;
		char[] s = str.toCharArray();
		int lt = 0, rt = str.length() - 1;
		while (lt < rt) {
			if (!Character.isAlphabetic(s[lt]))
				lt++;
			else if (!Character.isAlphabetic(s[rt]))
				rt--;
			else {
				char tmp = s[lt];
				s[lt] = s[rt];
				s[rt] = tmp;
				lt++;
				rt--;
			}
		}
		answer = String.valueOf(s);
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.next();

		System.out.println(T.solution(str));
	}

}
```
## 6. 중복문자제거
```
	public String solution(String str) {
		String answer = "";
		for (int i = 0; i < str.length(); i++) {
			if (str.indexOf(str.charAt(i)) == i)
				answer += str.charAt(i);

		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.next();
		System.out.println(T.solution(str));
	}

}
```
