## 1. 큰 수 출력하기

## 2. 보이는 학생

## 3. 가위바위보

## 4. 피보나치수열

## 5. 소수(에라토스테네스 체)

## 6. 뒤집은 소수

## 7. 점수계산

## 8. 등수구하기


# 정답

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
		int answer = 1, max = arr[0];
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
		System.out.print(T.solution(n, arr));
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
		for (char x : T.solution(n, a, b).toCharArray())
			System.out.println(x);

	}

}
```
## 4. 피보나치수열
```
	public int[] solution(int n) {
		int[] answer = new int[n];
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
		for (int i = 2; i < n; i++) { //0과1는 소수의 대상이 아니므로 인덱스 2부터 시작, n까지(<)
			if (ch[i] == 0) { //i가 0이
				answer++;
				for (int j = i; j < n; j = j + i)
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
```
