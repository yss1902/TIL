## 1. 선택정렬
```
	public int[] solution(int n, int[] arr) {
		for (int i = 0; i < n - 1; i++) { //마지막은바꿀필요없음
			int idx = i; //i값으로초기화(인덱스0), 이중포문이용
			for (int j = i + 1; j < n; j++) {
				if (arr[j] < arr[idx])
					idx = j;
			} //j-for문=i번째에서끝까지가장작은숫자의인덱스번호가idx에저장)
			int tmp = arr[i];
			arr[i] = arr[idx];
			arr[idx] = tmp; //교체완료
		}
		return arr;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++)
			arr[i] = kb.nextInt();
		for (int x : T.solution(n, arr))
			System.out.print(x + " ");
	}
}
```
## 2. 버블정렬
```
	public int[] solution(int n, int[] arr) {
		for (int i = 0; i < n - 1; i++) {
			for (int j = 0; j < n - i - 1; j++) { //i가하나씩커지니j는하나씩감소
				if (arr[j] > arr[j + 1]) {
					int tmp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = tmp;
				}
			}
		}
		return arr;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++)
			arr[i] = kb.nextInt();
		for (int x : T.solution(n, arr))
			System.out.print(x + " ");
	}
}
```
## 3. 삽입정렬
```
	public int[] solution(int n, int[] arr) {
		for (int i = 1; i < n; i++) { //두번째인덱스를기준으로
			int tmp = arr[i], j; //j를여기서선언해야아래사용가능
			for (j = i - 1; j >= 0; j--) { 
				if (arr[j] > tmp)
					arr[j + 1] = arr[j]; //뒤쪽으로민다
				else
					break;
			}
			arr[j + 1] = tmp; //사용가능,j가멈춘지점에tmp삽입
		}
		return arr;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++)
			arr[i] = kb.nextInt();
		for (int x : T.solution(n, arr))
			System.out.print(x + " ");
	}
}
```
## 4. LRU(캐시, 카카오 변형)
```
	public int[] solution(int size, int n, int[] arr) {
		int[] cache = new int[size];
		for (int x : arr) { //작업번호가하나하나x
			int pos = -1; //인덱스번호
			for (int i = 0; i < size; i++)
				if (x == cache[i]) //캐시히트
					pos = i;
			if (pos == -1) { //캐시미스
				for (int i = size - 1; i >= 1; i--) {
					cache[i] = cache[i - 1];
				}
			} else {
				for (int i = pos; i >= 1; i--) {
					cache[i] = cache[i - 1];
				}
			}
			cache[0] = x;
		}
		return cache;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int s = kb.nextInt();
		int n = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++)
			arr[i] = kb.nextInt();
		for (int x : T.solution(s, n, arr))
			System.out.print(x + " ");
	}
}
```
