## 1. 재귀함수(스택프레임)
```
class Main {
	public void DFS(int n) { //여기서부터시작(3)
		if (n == 0)
			return; //리턴하면종료.스텍D(0)은 10라인으로간다.
		else {
			DFS(n - 1);
			System.out.print(n + " ");
		}
	} //스택의상단이작동하고있으니1부터출력된다!

	public void solution(int n) {
		DFS(n);
	}

	public static void main(String[] args) {
		Main T = new Main();
		T.solution(3);
	}
}
```
## 2. 이진수 출력(재귀)
```
class Main {
	public void DFS(int n) {
		if (n == 0)
			return;
		else {
			DFS(n / 2);
			System.out.print(n % 2);
		}
	}

	public void solution(int n) {
		DFS(n);
	}

	public static void main(String[] args) {
		Main T = new Main();
		T.solution(11);
		
	}
}
```
## 3. 팩토리얼
```
class Main {
	public int DFS(int n) {
		if (n == 1)
			return 1;
		else
			return n * DFS(n - 1);
	}

	public static void main(String[] args) {
		Main T = new Main();
		System.out.println(T.DFS(5));
	}
}
```
## 4. 피보나치 재귀(메모이제이션)
```
class Main { //일반재귀
	public int DFS(int n){
		if(n==1) return 1;
		else if(n==2) return 1;
		else return DFS(n-2)+DFS(n-1);
	}
	public static void main(String[] args){
		Main T = new Main();
		int n=10;
		for(int i=1; i<=n; i++) System.out.print(T.DFS(i)+" ");
	}	
}


class Main { //메모라이제이션재귀
	static int[] fibo;

	public int DFS(int n) {
		if (fibo[n] > 0)
			return fibo[n];
		if (n == 1)
			return fibo[n] = 1;
		else if (n == 2)
			return fibo[n] = 1;
		else
			return fibo[n] = DFS(n - 2) + DFS(n - 1);
	}

	public static void main(String[] args) {
		Main T = new Main();
		int n = 45;
		fibo = new int[n + 1];
		T.DFS(n);
		for (int i = 1; i <= n; i++)
			System.out.print(fibo[i] + " ");
	}
}
```
## 5. 이진트리순회(DFS : Depth-First Search)
```
class Node {
	int data;
	Node lt, rt;

	public Node(int val) {
		data = val;
		lt = rt = null;
	}
}

public class Main {
	Node root;

	public void DFS(Node root) {
		if (root == null) //말단노드로왔으니종료
			return;
		else {
			DFS(root.lt);
			System.out.print(root.data + " "); //위치에따라 (전중후)위순회
			DFS(root.rt);
		}
	}

	public static void main(String args[]) {
		Main tree = new Main();
		tree.root = new Node(1);
		tree.root.lt = new Node(2);
		tree.root.rt = new Node(3);
		tree.root.lt.lt = new Node(4);
		tree.root.lt.rt = new Node(5);
		tree.root.rt.lt = new Node(6);
		tree.root.rt.rt = new Node(7);
		tree.DFS(tree.root);
	}
}
```
## 6. 부분집합 구하기(DFS)
```
class Main {
	static int n;
	static int[] ch;

	public void DFS(int L) {
		if (L == n + 1) { //종착지점에도달(3의경우4생성지점)
			String tmp = "";
			for (int i = 1; i <= n; i++) {
				if (ch[i] == 1)
					tmp += (i + " ");
			}
			if (tmp.length() > 0) //공집합이아니면출력
				System.out.println(tmp);
		} else {
			ch[L] = 1;
			DFS(L + 1); //왼쪽으로 뻗음,사용한다
			ch[L] = 0;
			DFS(L + 1); //오른쪽으로 뻗음,사용하지않음
		}
	}

	public static void main(String[] args) {
		Main T = new Main();
		n = 3;
		ch = new int[n + 1];
		T.DFS(1);
	}
}
```
## 7. 이진트리 레벨탐색(BFS : Breadth-First Search)
```
class Node {
	int data;
	Node lt, rt;

	public Node(int val) {
		data = val;
		lt = rt = null;
	}
}

public class Main {
	Node root;

	public void BFS(Node root) {
		Queue<Node> Q = new LinkedList<>();
		Q.add(root); //100번지삽입
		int L = 0; //루트노드(레벨)는0
		while (!Q.isEmpty()) {
			int len = Q.size();
			System.out.print(L + " : "); //이레벨에어떤노드가있는지출력
			for (int i = 0; i < len; i++) { //원소갯수(Q레벨)만큼
				Node cur = Q.poll(); //현재노드의앞에것을꺼냄
				System.out.print(cur.data + " "); //100번지의data출력(1)
				if (cur.lt != null) //현재노드왼쪽자식이null이아니면
					Q.add(cur.lt);
				if (cur.rt != null)
					Q.add(cur.rt);
			} //레벨이끝남
			L++; //레벨증가
			System.out.println();
		}
	}

	public static void main(String args[]) {
		Main tree = new Main(); //그린그림과같음
		tree.root = new Node(1);
		tree.root.lt = new Node(2);
		tree.root.rt = new Node(3);
		tree.root.lt.lt = new Node(4);
		tree.root.lt.rt = new Node(5);
		tree.root.rt.lt = new Node(6);
		tree.root.rt.rt = new Node(7);
		tree.BFS(tree.root); //BFS.루트노드(100번지를가르킴)
	}
}
```
## 8. 송아지 찾기1(BFS)
```
class Main {
	int answer = 0;
	int[] dis = { 1, -1, 5 };
	int[] ch; //체크배열:이미나온결과값을저장
	Queue<Integer> Q = new LinkedList<>();

	public int BFS(int s, int e) {
		ch = new int[10001]; //직선의좌표점(인덱스번호)
		ch[s] = 1; //출발지점
		Q.offer(s);
		int L = 0;
		while (!Q.isEmpty()) {
			int len = Q.size();
			for (int i = 0; i < len; i++) {
				int x = Q.poll();
				for (int j = 0; j < 3; j++) {
					int nx = x + dis[j]; //x의자신노드:nx
					if (nx == e) {
						return L + 1; //송아지를찾음(자식노드니까+1)
					}
					if (nx >= 1 && nx <= 10000 && ch[nx] == 0) {
						ch[nx] = 1; //범위안에서방문안한노드찾기,방문했다.
						Q.offer(nx);
					}
				}
			}
			L++; //레벨증가
		}
		return 0;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int s = kb.nextInt();
		int e = kb.nextInt();
		System.out.println(T.BFS(s, e));
	}
}
```
## 10. Tree 말단노드까지의 까장 짧은 경로(BFS)
