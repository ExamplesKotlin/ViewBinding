# ViewBindig

### Activity

1.- Activar el View Binding:

En el gradle de Application (gradle del Modulo), dentro de android:

```
android {
    compileSdkVersion 30
    buildToolsVersion "30.0.2"

...
    kotlinOptions {
        jvmTarget = '1.8'
    }
    
//     viewBinding { enabled = true } // Deprecated

    buildFeatures {
        viewBinding = true   //  👈🏽
    }

}

dependencies {
...
```

Ahora:

activity_main.xml -> ActivityMainBinding

EL MainActivity quedaria asi:

```
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // From Here 👇🏼
        val binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
    }
}
```


### Fragment

Consider that fragment call `result_profile.xml`
```
private var _binding: ResultProfileBinding? = null
// This property is only valid between onCreateView and
// onDestroyView.
private val binding get() = _binding!!

override fun onCreateView(
    inflater: LayoutInflater,
    container: ViewGroup?,
    savedInstanceState: Bundle?
): View? {
    _binding = ResultProfileBinding.inflate(inflater, container, false)
    val view = binding.root
    return view
}

override fun onDestroyView() {
    super.onDestroyView()
    _binding = null
}
```
