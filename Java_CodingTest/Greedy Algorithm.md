## 1. 씨름선수
```
import java.util.*;

class Body implements Comparable<Body> {
	public int h, w;

	Body(int h, int w) {
		this.h = h;
		this.w = w;
	}

	@Override //h에서 내림차순 된다
	public int compareTo(Body o) {
		return o.h - this.h;
	}
}

class Main {
	public int solution(ArrayList<Body> arr, int n) {
		int cnt = 0;
		Collections.sort(arr);
		int max = Integer.MIN_VALUE;
		for (Body ob : arr) {
			if (ob.w > max) {
				max = ob.w;
				cnt++;
			}
		}
		return cnt;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		ArrayList<Body> arr = new ArrayList<>();
		for (int i = 0; i < n; i++) {
			int h = kb.nextInt();
			int w = kb.nextInt();
			arr.add(new Body(h, w));
		}
		System.out.println(T.solution(arr, n));
	}
}
```

## 2. 회의실 배정
```
import java.util.*;

class Time implements Comparable<Time> {
	public int s, e;

	Time(int s, int e) {
		this.s = s;
		this.e = e;
	}

	@Override //끝나는 시간이 같으면 시작시간을 오름차순한다.
	public int compareTo(Time o) {
		if (this.e == o.e)
			return this.s - o.s;
		else
			return this.e - o.e;
	}
}

class Main {
	public int solution(ArrayList<Time> arr, int n) {
		int cnt = 0;
		Collections.sort(arr);
		int et = 0;
		for (Time ob : arr) {
			if (ob.s >= et) {
				cnt++;
				et = ob.e;
			}
		}
		return cnt;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		ArrayList<Time> arr = new ArrayList<>();
		for (int i = 0; i < n; i++) {
			int x = kb.nextInt();
			int y = kb.nextInt();
			arr.add(new Time(x, y));
		}
		System.out.println(T.solution(arr, n));
	}
}
```
## 3. 결혼식
```
import java.util.*;

class Time implements Comparable<Time> {
	public int time;
	public char state;

	Time(int time, char state) {
		this.time = time;
		this.state = state;
	}

	@Override
	public int compareTo(Time ob) {
		if (this.time == ob.time)
			return this.state - ob.state;
		else
			return this.time - ob.time;
	}
}

class Main {
	public int solution(ArrayList<Time> arr) {
		int answer = Integer.MIN_VALUE;
		Collections.sort(arr);
		int cnt = 0;
		for (Time ob : arr) {
			if (ob.state == 's')
				cnt++;
			else
				cnt--;
			answer = Math.max(answer, cnt);
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		ArrayList<Time> arr = new ArrayList<>();
		for (int i = 0; i < n; i++) {
			int sT = kb.nextInt();
			int eT = kb.nextInt();
			arr.add(new Time(sT, 's'));
			arr.add(new Time(eT, 'e'));
		}
		System.out.println(T.solution(arr));
	}
}
```
