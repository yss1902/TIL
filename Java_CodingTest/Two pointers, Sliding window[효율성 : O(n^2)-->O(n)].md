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
			sum += (arr[i] - arr[i - k]);
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
