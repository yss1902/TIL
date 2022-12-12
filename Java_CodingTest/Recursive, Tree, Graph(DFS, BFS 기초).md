## 1. 재귀함수(스택프레임)
```
class Main {
	public void DFS(int n) {
		if (n == 0)
			return;
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
