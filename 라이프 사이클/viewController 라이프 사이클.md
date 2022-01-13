```swift

뷰컨트롤러는 우리가 접근 할 수 있는 특정 핵심순간이 있는 생명주기를 가지고있다.

그렇기 때문에 그 순간에 어떤 일이 일어나야 하는지를 지정하는 코드를 작성할수 있다.

1. 가장먼저 일어나는일은 @viewDidLoad 가 호출된다.

이녀석은 리소스를 초기화하거나 초기화면을 구성하는일을 한다. 컨트롤러가 메모리에 로드된후에 호출이된다.

2. 그다음엔 @viewWillAppear 가 호출된다.

이녀석은 화면이 나타날것이라는 신호를 컨트롤러에게 알리는 역할을한다.

viewDidLoad 랑 viewWillAppear 둘다 뷰가 나타기전에 호출되는건 맞지만

viewDidLoad는 컨트롤러에 메모리가 로드된후라면 다시 호출되지않는다.

viewWillAppear 화면이 나타나기전에는 무조건 계속 호출된다.

예시로 네비게이션 컨트롤러의 rootview인 첫번째 뷰는 한번만 호출이 된다.

3. 그다음엔 @viewDidAppear 가 호출된다.

이녀석은 뷰가 나타났다는 것을 컨트롤러에게 알리거나 애니메이션을 그리거나 하는 역학을 한다.

뷰가 화면에 나타난 직후에 실행된다.

viewWillAppear와 호출되는 시점이 다를뿐 거의 같다.

4. 그다음엔 @viewWillDisAppear 가 호출된다.

이녀석은 뷰가 사라지기 직전에 호출이된다.

컨트롤러에게 뷰가 삭제되려고 하고있는걸을 알리는 역할을 한다.

5. 마지막으로 @viewDidDisappear 가 호출된다.
viewDidDisappear는 viewWillDisAppear가 호출된 후에 컨트롤러에게 뷰가 제거되었음을 알려주는 녀석이다. 뷰 제거 직후

예시로 한번 보자면

//첫번째 뷰가 실행되면

1번째 viewDidLoad 호출
1번째 viewWillAppear 호출
1번째 화면 나타남
1번째 viewDidAppear 호출


//여기서 두번째 뷰로 넘어가게되면
1번째 viewWillDisappear 호출
2번째 viewDidLoad 호출
2번째 viewWillAppear 호출
1번째 화면 없어짐
1번째 viewDidDisappear 호출
2번째 화면 나타남
2번째 viewDidAppear 호출

//여기서 다시 첫번째뷰로 넘어가면
2번째 viewWillDisAppear 호출
1번째 viewDidLoad는 호출되지않고 (이미 컨트롤러의 메모리가 로드된 후 이기때문에 호출이 되지않음)
1번째 viewWillAppear 호출
2번째 화면 없어짐
2번째 viewDidDisappear 호출
1번쨰 화면 나타남
1번쨰 viewDidAppear 호출
```