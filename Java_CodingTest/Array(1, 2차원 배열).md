## 1. 큰 수 출력하기

## 2. 보이는 학생













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
