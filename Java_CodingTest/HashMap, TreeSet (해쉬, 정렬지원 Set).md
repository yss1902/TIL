## 1. 학급 회장
```
	public char solution(int n, String s) {
		char answer = ' ';
		HashMap<Character, Integer> map = new HashMap<>();
		for (char key : s.toCharArray()) {
			map.put(key, map.getOrDefault(key, 0) + 1); //중요. get은 x의 키 값을 가져옴.
		} // 없더라면 0을 리턴함.

		int max = Integer.MIN_VALUE;
		for (char key : map.keySet()) { //최대 밸류값의 키를 알아내기. 존재하는 키들을 탐색 set
			if (map.get(key) > max) { //키의 값을 가져옴 get
				max = map.get(key);
				answer = key;
			}
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		String str = kb.next();
		System.out.println(T.solution(n, str));
	}
}
```
