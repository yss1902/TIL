## 계단오르기
```
import java.util.*;

class Main {
	static int[] dy;

	public int solution(int n) {
		dy[1] = 1;
		dy[2] = 2;
		for (int i = 3; i <= n; i++)
			dy[i] = dy[i - 2] + dy[i - 1];
		return dy[n];
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		dy = new int[n + 1];
		System.out.print(T.solution(n));
	}
}
```
## 돌다리 건너기
```
import java.util.*;

class Main {
	static int[] dy;

	public int solution(int n) {
		dy[1] = 1;
		dy[2] = 2;
		for (int i = 3; i <= n + 1; i++)
			dy[i] = dy[i - 2] + dy[i - 1];
		return dy[n + 1]; //다리를 건너는 것은 끝까지 가야 하기 때문에 +1
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		dy = new int[n + 2];
		System.out.print(T.solution(n));
	}
}
```
