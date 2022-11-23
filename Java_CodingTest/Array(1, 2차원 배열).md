## 1. 큰 수 출력하기

```
public class Main_Sub {
	public ArrayList<Integer> solution(int n, int[] arr) { //정답값이 배열로 여러개 나와야 하므로..
		ArrayList<Integer> answer = new ArrayList<>();
		answer.add(arr[0]);
		for (int i = 1; i < n; i++) {
			if (arr[i] > arr[i - 1])
				answer.add(arr[i]);
		}

		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) { // 입력받는 n의 수만큼만 입력받아야 하므로 배열 arr에 들어가는 횟수를 정함
			arr[i] = sc.nextInt(); // 이후 arr에 값을 입력받는다
		}
		for (int x : T.solution(n, arr)) { // arr값이므로 x에 하나씩 할당한 다음 넘긴다. 공백 만들고.
			System.out.print(x + " ");
		}

	}

}
```
## 2. 보이는 학생

```
	public int solution(int n, int[] arr) {
		int answer = 1, max = arr[0]; //첫번째 사람은 무조건 보이니까 1, 맥스값을 0번 인덱스로 우선 지정
		for (int i = 1; i < n; i++) { //i(인덱스)는 1번부터(2번째사람부터), i는 n번째 사람까지, 한번씩돈다.
			if (arr[i] > max) { //만약 i번째 사람이 max값보다 크면 answer에 1증가하고 max값을 arr[i]로 바꾼다.
				answer++;
				max = arr[i];
			}

		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(T.solution(n, arr)); //답은 개수만 출력하는 거니까 이런 형식으로
	}

}
```
## 3. 가위바위보
```
	public String solution(int n, int[] a, int[] b) {
		String answer = "";
		for (int i = 0; i < n; i++) {
			if (a[i] == b[i])
				answer += "D";
			else if (a[i] == 1 && b[i] == 3)
			 	answer += "A";
			else if (a[i] == 2 && b[i] == 1)
				answer += "A";
			else if (a[i] == 3 && b[i] == 2)
				answer += "A";
			else
				answer += "B";
		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] a = new int[n];
		int[] b = new int[n];
		for (int i = 0; i < n; i++) {
			a[i] = sc.nextInt();
		}
		for (int i = 0; i < n; i++) {
			b[i] = sc.nextInt();
		}
		for (char x : T.solution(n, a, b).toCharArray()) //스트링을 배열char화 시켜서 x에 대입시킨다.(정답이 세로로 나오게)
			System.out.println(x);

	}

}
```
## 4. 피보나치수열
```
	public int[] solution(int n) { //배열로 받는다.
		int[] answer = new int[n]; //답을 받을 answer배열을 만든다.
		answer[0] = 1;
		answer[1] = 1;
		for (int i = 2; i < n; i++) {
			answer[i] = answer[i - 2] + answer[i - 1];
		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		for (int x : T.solution(n))
			System.out.print(x + " ");

	}

}
```
## 5. 소수(에라토스테네스 체)
```
	public int solution(int n) {
		int answer = 0;
		int[] ch = new int[n + 1]; //n번 인덱스까지 생성하기 위해 플1
		for (int i = 2; i <= n; i++) { //0과1는 소수의 대상이 아니므로 인덱스 2부터 시작, n까지(<=)
			if (ch[i] == 0) { //i가 0이면 소수임, 그리고 i의 배수를 체크해야 함 
				answer++;
				for (int j = i; j < n; j = j + i) //그리고 i의 배수를 체크해야 함, j=j+i는 j는i의 배수로 돈다. 만약 j+2면 2의 배수) 
					ch[j] = 1;
			}
		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		System.out.println(T.solution(n));

	}

}
```
## 6. 뒤집은 소수
```
public class Main_Sub {
	public boolean isPrime(int num) {
		if (num == 1)
			return false;
		for (int i = 2; i < num; i++) {
			if (num % i == 0)
				return false;
		}
		return true;
	}

	public ArrayList<Integer> solution(int n, int[] arr) {
		ArrayList<Integer> answer = new ArrayList<>();
		for (int i = 0; i < n; i++) {
			int tmp = arr[i];
			int res = 0;
			while (tmp > 0) {
				int t = tmp % 10;
				res = res * 10 + t;
				tmp = tmp / 10;
			}
			if (isPrime(res))
				answer.add(res);
		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		for (int x : T.solution(n, arr)) {
			System.out.print(x + " "); 

		}

	}
}
```
## 7. 점수계산
```
	public int solution(int n, int[] arr) {
		int answer = 0;
		int cnt = 0;

		for (int i = 0; i < n; i++) {
			if (arr[i] == 1) {
				cnt++;
				answer += cnt;
			} else
				cnt = 0;
		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		System.out.print(T.solution(n, arr));

	}
}
```
## 8. 등수구하기
```
	public int[] solution(int n, int[] arr) {
		int[] answer = new int[n];
		for (int i = 0; i < n; i++) {
			int cnt = 1;
			for (int j = 0; j < n; j++) {
				if (arr[j] > arr[i])
					cnt++;
			}
			answer[i] = cnt;
		}
		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		for (int x : T.solution(n, arr))
			System.out.print(x + " ");

	}
}
```

## 9. 격자판 최대합
```
	public int solution(int n, int[][] arr) {
		int answer = Integer.MIN_VALUE;
		int sum1, sum2;
		for (int i = 0; i < n; i++) {
			sum1 = sum2 = 0;
			for (int j = 0; j < n; j++) {
				sum1 += arr[i][j];
				sum2 += arr[j][i];
			}
			answer = Math.max(answer, sum1);
			answer = Math.max(answer, sum2);
		}
		sum1 = sum2 = 0;
		for (int i = 0; i < n; i++) {
			sum1 += arr[i][i];
			sum2 += arr[i][n - i - 1];
		}
		answer = Math.max(answer, sum1);
		answer = Math.max(answer, sum2);

		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[][] arr = new int[n][n];
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				arr[i][j] = sc.nextInt();
			}
		}

		System.out.print(T.solution(n, arr));

	}
}
```

## 10. 봉우리
```
public class Main_Sub {
	int[] dx = { -1, 0, 1, 0 };
	int[] dy = { 0, 1, 0, -1 };

	public int solution(int n, int[][] arr) {
		int answer = 0;
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				boolean flag = true;
				for (int k = 0; k < 4; k++) {
					int nx = i + dx[k];
					int ny = j + dy[k];
					if (nx >= 0 && nx < n && ny >= 0 && ny < n && arr[nx][ny] >= arr[i][j]) {
						flag = false;
						break;
					}
				}
				if (flag)
					answer++;
			}
		}

		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[][] arr = new int[n][n];
		for (int i = 0; i < n; i++) {
			for (int j = 0; j < n; j++) {
				arr[i][j] = sc.nextInt();
			}
		}

		System.out.print(T.solution(n, arr));

	}
}
```

## 11. 임시반장 정하기
```
	public int solution(int n, int[][] arr) {
		int answer = 0;
		int max = Integer.MIN_VALUE;
		for (int i = 1; i <= n; i++) {
			int cnt = 0;
			for (int j = 1; j <= n; j++) {
				for (int k = 1; k <= 5; k++) {
					if (arr[i][k] == arr[j][k]) {
						cnt++;
						break;
					}
				}
			}
			if (cnt > max) {
				max = cnt;
				answer = i;
			}
		}

		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int[][] arr = new int[n + 1][6];
		for (int i = 1; i <= n; i++) {
			for (int j = 1; j <= 5; j++) {
				arr[i][j] = sc.nextInt();
			}
		}

		System.out.print(T.solution(n, arr));

	}
}
```

## 12. 멘토링
```
	public int solution(int n, int m, int[][] arr) {
		int answer = 0;
		for (int i = 1; i <= n; i++) {
			for (int j = 1; j <= n; j++) {
				int cnt = 0;
				for (int k = 0; k < m; k++) {
					int pi = 0, pj = 0;
					for (int s = 0; s < n; s++) {
						if (arr[k][s] == i)
							pi = s;
						if (arr[k][s] == j)
							pj = s;
					}
					if (pi < pj)
						cnt++;
				}
				if (cnt == m) {
					answer++;
				}
			}
		}

		return answer;
	}

	public static void main(String[] args) {

		Main_Sub T = new Main_Sub();
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[][] arr = new int[m][n];
		for (int i = 0; i < m; i++) {
			for (int j = 0; j < n; j++) {
				arr[i][j] = sc.nextInt();
			}
		}

		System.out.print(T.solution(n, m, arr));

	}
}
```
