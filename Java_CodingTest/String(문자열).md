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
## 7. 회문문자열
```
	public String solution(String str) {
		String answer = "YES";
		int len = str.length();
		for (int i = 0; i < len / 2; i++) {
			if (str.charAt(i) != str.charAt(len - i - 1))
				return "NO";
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
## 8. 유효한 팰린드룸
```
	public String solution(String s) {
		String answer = "NO";
		s = s.toUpperCase().replaceAll("[^A-Z]", ""); //A부터Z까지가 아닌것들을 빈문자 해라
		String tmp = new StringBuilder(s).reverse().toString();
		if (s.equals(tmp))
			answer = "YES";
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.nextLine();
		System.out.println(T.solution(str));
	}

}
```
## 9. 숫자만 추출
```
	public int solution(String s) {
		int answer = 0;
		for (char x : s.toCharArray()) {
			if (x >= 48 && x <= 57) //아스키코드(48은0, 57은9)
				answer = answer * 10 + (x - 48); //숫자만추출하여이어붙이는식
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
## 10. 가장 짧은 문자거리
```
	public int[] solution(String s, char t) {
		int[] answer = new int[s.length()];
		int p = 1000;
		for (int i = 0; i < s.length(); i++) {
			if (s.charAt(i) == t) {
				p = 0;
				answer[i] = p;
			} else {
				p++;
				answer[i] = p; // 왼쪽에있는e의for문
			}
		}
		p = 1000;
		for (int i = s.length() - 1; i >= 0; i--) { // 오른쪽for문과비교해작은것으로교체
			if (s.charAt(i) == t) {
				p = 0;
				answer[i] = p;
			} else {
				p++;
				answer[i] = Math.min(answer[i], p); // 기존값과p중에서작은값으로
			}
		}
		return answer;

	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		String str = sc.next();
		char c = sc.next().charAt(0);
		for (int x : T.solution(str, c)) {
			System.out.print(x + " ");
		}

	}

}
```
## 11. 문자열 압축
```
	public String solution(String s) {
		String answer = "";
		s = s + " "; //맨뒤 공백을 만들고
		int cnt = 1;
		for (int i = 0; i < s.length() - 1; i++) { // i는 빈문자 전까지만 가야하니까 -1
			if (s.charAt(i) == s.charAt(i + 1))
				cnt++;
			else {
				answer += s.charAt(i);
				if (cnt > 1)
					answer += String.valueOf(cnt);
				cnt = 1;
			}
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
## 12. 암호
```
	public String solution(int n, String s) {
		String answer = "";
		for (int i = 0; i < n; i++) {
			String tmp = s.substring(0, 7).replace('#', '1').replace('*', '0');
			int num = Integer.parseInt(tmp, 2); //인자를 tmp로 넘어가고 2진수화
			answer += (char) num;
			s = s.substring(7);
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		String str = sc.next();
		System.out.print(T.solution(n, str));
	}

}
```
