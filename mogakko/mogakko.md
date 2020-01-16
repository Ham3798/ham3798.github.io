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
![리스트뷰](./mogakko/1.png)

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
