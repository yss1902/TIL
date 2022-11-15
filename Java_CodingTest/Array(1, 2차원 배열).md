## 1. 큰 수 출력하기















# 정답

## 1. 큰 수 출력하기

```
public class Main_Sub {
	public ArrayList<Integer> solution(int n, int[] arr) {
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
			arr[i] = sc.nextInt();
		}
		for (int x : T.solution(n, arr)) {
			System.out.print(x + " ");
		}

	}

}
```
