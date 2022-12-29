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
## 4. 최대수입 스케쥴
```
import java.util.*;

class Lecture implements Comparable<Lecture> {
	public int money;
	public int date;

	Lecture(int money, int date) {
		this.money = money;
		this.date = date;
	}

	@Override
	public int compareTo(Lecture ob) {
		return ob.date - this.date;
	}
}

class Main {
	static int n, max = Integer.MIN_VALUE;

	public int solution(ArrayList<Lecture> arr) {
		int answer = 0;
		PriorityQueue<Integer> pQ = new PriorityQueue<>(Collections.reverseOrder());
		Collections.sort(arr);
		int j = 0;
		for (int i = max; i >= 1; i--) {
			for (; j < n; j++) {
				if (arr.get(j).date < i)
					break;
				pQ.offer(arr.get(j).money);
			}
			if (!pQ.isEmpty())
				answer += pQ.poll();
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		n = kb.nextInt();
		ArrayList<Lecture> arr = new ArrayList<>();
		for (int i = 0; i < n; i++) {
			int m = kb.nextInt();
			int d = kb.nextInt();
			arr.add(new Lecture(m, d));
			if (d > max)
				max = d;
		}
		System.out.println(T.solution(arr));
	}
}
```
