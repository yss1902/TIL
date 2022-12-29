## 1. 두 배열 합치기(two pointers algorithm)
```
	public ArrayList<Integer> solution(int n, int m, int[] a, int[] b) {
		ArrayList<Integer> answer = new ArrayList<>();
		int p1 = 0, p2 = 0;
		while (p1 < n && p2 < m) { // 둘중하나라도거짓이라면 와일문은멈춘다
			if (a[p1] < b[p2])
				answer.add(a[p1++]); // p1값이add되고 p1값1증가
			else
				answer.add(b[p2++]);
		}
		while (p1 < n) //둘중무엇이먼저끝났는지모르므로..둘다적용
			answer.add(a[p1++]);
		while (p2 < m)
			answer.add(b[p2++]);
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] a = new int[n];
		for (int i = 0; i < n; i++) {
			a[i] = sc.nextInt();
		}
		int m = sc.nextInt();
		int[] b = new int[m];
		for (int i = 0; i < m; i++) {
			b[i] = sc.nextInt();
		}
		for (int x : T.solution(n, m, a, b))
			System.out.print(x + " ");
	}

}
```
## 2. 공통원소구하기(two pointers algorithm)
```
	public ArrayList<Integer> solution(int n, int m, int[] a, int[] b) { //교집합이용
		ArrayList<Integer> answer = new ArrayList<>();
		Arrays.sort(a);
		Arrays.sort(b);
		int p1 = 0, p2 = 0;
		while (p1 < n && p2 < m) {
			if (a[p1] == b[p2]) {
				answer.add(a[p1++]); // p1이나p2아무거나가능
				p2++;
			} else if (a[p1] < b[p2]) // 작은쪽을증가시킨다
				p1++;
			else
				p2++;

		}
		return answer;

	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] a = new int[n];
		for (int i = 0; i < n; i++) {
			a[i] = sc.nextInt();
		}
		int m = sc.nextInt();
		int[] b = new int[m];
		for (int i = 0; i < m; i++) {
			b[i] = sc.nextInt();
		}
		for (int x : T.solution(n, m, a, b))
			System.out.print(x + " ");
	}

}
```
## 3. 최대 매출(Sliding window)
```
	public int solution(int n, int k, int[] arr) {
		int answer = 0, sum = 0;
		for (int i = 0; i < k; i++) //우선 첫번째 sum값을 구한다
			sum += arr[i];
		answer = sum;
		for (int i = k; i < n; i++) { //k부터 시작
			sum += (arr[i] - arr[i - k]); //i와 i뒤 2칸값을 빼는 것임
			answer = Math.max(answer, sum); //기본값과썸값에서큰값으로리턴
		}

		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(T.solution(n, k, arr));
	}

}
```
## 4. 연속 부분수열(복합적 문제)
```
	public int solution(int n, int m, int[] arr) {
		int answer = 0, sum = 0, lt = 0;
		for (int rt = 0; rt < n; rt++) { //rt가진행
			sum += arr[rt]; //우선 더하고
			if (sum == m)
				answer++;
			while (sum >= m) { //sum값이m보다크거나같으면 왼쪽lt값을뺀다음에증가
				sum -= arr[lt++];
				if (sum == m)
					answer++;
			}

		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(T.solution(n, m, arr));
	}

}
```
## 5. 연속된 자연수의 합(two pointers)
```
	public int solution(int n) {
		int answer = 0, sum = 0, lt = 0;
		int m = n / 2 + 1;
		int[] arr = new int[m];
		for (int i = 0; i < m; i++)
			arr[i] = i + 1;
		for (int rt = 0; rt < m; rt++) {
			sum += arr[rt];
			if (sum == n)
				answer++;
			while (sum >= n) {
				sum -= arr[lt++];
				if (sum == n)
					answer++;
			}
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();

		System.out.print(T.solution(n));
	}

}
```
## 5. 연속된 자연수의 합(수학)
```
	public int solution(int n) {
		int answer = 0, cnt = 1;
		n--; //우선1을먼저뺌
		while (n > 0) { //n이0보다높으면참
			cnt++;
			n = n - cnt; //여기서2를뺌
			if (n % cnt == 0)
				answer++;
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		System.out.print(T.solution(n));
	}

}
```
## 6. 최대 길이 연속부분수열(복합적 문제)
```
	public int solution(int n, int k, int[] arr) {
		int answer = 0, cnt = 0, lt = 0; //cnt=0을1로바꾼횟수
		for (int rt = 0; rt < n; rt++) {
			if (arr[rt] == 0)
				cnt++;
			while (cnt > k) { //k(체인지가능횟수)보다크면안됨
				if (arr[lt] == 0) //lt가가르키는곳이0이면
					cnt--; //cnt감소시키고
				lt++; //lt증가
			}
			answer = Math.max(answer, rt - lt + 1);
		} //정답과 (연속되는 최대수열길이)에서의 큰 값
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int k = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}

		System.out.print(T.solution(n, k, arr));
	}

}
```
