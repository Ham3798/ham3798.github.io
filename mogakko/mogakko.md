## 모각코 1일차. 2020.01.14

오늘은 첫 번째 모각코 모임을 가졌습니다.
같이 주니어 소프트웨어 대회를 참가하기 때문에 이를 만들기 위한 사전 지식을 쌓는 시간을 각자 갖기로 했습니다.
인프런 강의를 통해 공부함.

```markdown
오늘의 목표
android studio

1. 리스트 뷰
2. 액티비티 화면 전환
3. 버튼 이미지 애니메이션
4. 레이아웃
```

1. 리스트 뷰
- 안드로이드 ListView ListView는 사용자가 정의한 데이터 목록을 아이템 단위로 구성하여 화면에 출력하는 ViewGroup의 한 종류

![1](./mogakko/1.png)

```markdown
public class ImageAdapter extends ArrayAdapter<String> {
    ImageAdapter(Context context, String[] items) {
        super(context, R.layout.image_layout, items);
    }

    @NonNull
    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        LayoutInflater imageInflater = LayoutInflater.from(getContext());
        View view = imageInflater.inflate(R.layout.image_layout, parent, false);
        String item = getItem(position);
        TextView textView = (TextView) view.findViewById(R.id.textView);
        ImageView imageView = (ImageView) view.findViewById(R.id.imageView);
        textView.setText(item);
        imageView.setImageResource(R.mipmap.ic_launcher);
        return view;
    }
}
```
```markdown
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        String[] Items = {"설정", "으아아", "망고"};
        ListAdapter adapter = new ImageAdapter(this, Items);
        ListView listView = (ListView) findViewById(R.id.listView);
        listView.setAdapter(adapter);

        listView.setOnItemClickListener(
                new AdapterView.OnItemClickListener() {
                    @Override
                    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                        String item = String.valueOf(parent.getItemAtPosition(position));
                        Toast.makeText(MainActivity.this, item, Toast.LENGTH_SHORT).show();
                    }
                }
        );
    }
}
```

일반적인 리스트뷰의 각각에 이미지를 추가하기 위해 ImageAdapter class를 만들어서 이미지를 넣은 리스트뷰의 레이아웃을 구성하고 이를 MainActivity class로 리스트뷰를 구성.

2. 액티비티 화면 전환
- 안드로이드 스튜디오에서 여러개의 액티비티와 그에 따른 각각의 레이아웃을 생성하고 액티비티에 의해 다른 레이아웃으로 전환하도록 작성함.

3. 버튼 이미지 애니메이션
- 특정 이미지를 통해 버튼을 생성해서 특정 조건에 따라 버튼의 이미지가 달라지게 함.

4. 레이아웃
- 흔히 알고 있는 그리드 레이아웃부터 Linear, Horizontal 레이아웃 등을 공부함.


## 모각코 2일차. 2020.01.16

짦지만 그동안 공부한 내용과 더불어 주니어 소프트웨어 대회에 제출할 앱을 대략적으로 만들어 보려고 함.
우선은 로그인 시스템과 우리가 계획한 레이아웃을 꾸미는 것이 목표.
