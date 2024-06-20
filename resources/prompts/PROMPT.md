# PROMPT (Título)
Crie um título de um ebook sobre o tema Google Android, o ebook é do nicho de programação e o subnicho é kotlin, o título deve ser impactante e curto, que tenha como temática dicas no título, me liste 5 variações de título

Claro! Aqui estão cinco variações de título para o seu ebook sobre Google Android com foco em Kotlin, com a temática de dicas no título:

1. **"Dicas Poderosas de Kotlin para Android"**
2. **"Kotlin para Android: Dicas Essenciais"**
3. **"Dicas de Mestre: Kotlin no Android"**
4. **"Kotlin Android: Truques e Dicas"**
5. **"Segredos Kotlin: Dicas para Desenvolvedores Android"**

# PROMPT (Conteúdo)

Faça um texto para ebook, com foco em kotlin, listando as principais Extensions para Android com exemplos em código

{REGRAS}

Explique sempre de uma maneira simples
Deixe o texto enxuto
Sempre traga exemplos de código em contextos reais
Sempre deixe um título sugestivo por tópico
Faça 02 exemplos para cada um dos tópicos
Crie tópicos com os temas: View, Context, String, SharedPreferences, Deeplink, Concorrência, Http Request, Json, attribs

# Extensions Essenciais em Kotlin para Android

Neste ebook, vamos explorar algumas das extensões mais úteis em Kotlin para Android. Extensions ajudam a simplificar o código e aumentar a produtividade. Vamos ver exemplos práticos para cada tipo de extensão.

## 1. View

### Simplificando o Acesso a Views

Com as extensions, podemos evitar a repetição de chamadas a `findViewById`.

```kotlin
// Antes
val textView = findViewById<TextView>(R.id.textView)
textView.text = "Hello, World!"

// Depois
fun Activity.setTextViewText(id: Int, text: String) {
    findViewById<TextView>(id).text = text
}

setTextViewText(R.id.textView, "Hello, World!")
```

### Clique Simplificado

Podemos criar uma extensão para configurar um clique em uma view de forma mais simples.

```kotlin
fun View.onClick(action: () -> Unit) {
    setOnClickListener { action() }
}

// Uso
button.onClick {
    // Ação a ser executada no clique
    Toast.makeText(this, "Button Clicked!", Toast.LENGTH_SHORT).show()
}
```

## 2. Context

### Mostrar Toast com Facilidade

Podemos criar uma extensão para exibir toasts de forma simplificada.

```kotlin
fun Context.showToast(message: String, duration: Int = Toast.LENGTH_SHORT) {
    Toast.makeText(this, message, duration).show()
}

// Uso
context.showToast("Hello, World!")
```

### Obter Color

Podemos criar uma extensão para obter cores de recursos de forma mais direta.

```kotlin
fun Context.getColorCompat(id: Int): Int {
    return ContextCompat.getColor(this, id)
}

// Uso
val color = context.getColorCompat(R.color.myColor)
```

## 3. String

### Validação de Email

Podemos criar uma extensão para verificar se uma string é um email válido.

```kotlin
fun String.isValidEmail(): Boolean {
    return Patterns.EMAIL_ADDRESS.matcher(this).matches()
}

// Uso
val email = "example@gmail.com"
if (email.isValidEmail()) {
    // Email válido
}
```

### Capitalização

Podemos criar uma extensão para capitalizar a primeira letra de uma string.

```kotlin
fun String.capitalizeFirstLetter(): String {
    return this.substring(0, 1).uppercase() + this.substring(1)
}

// Uso
val text = "hello"
val capitalizedText = text.capitalizeFirstLetter()
```

## 4. SharedPreferences

### Gravar Dados

Podemos criar uma extensão para salvar dados nas SharedPreferences.

```kotlin
fun SharedPreferences.put(key: String, value: String) {
    edit().putString(key, value).apply()
}

// Uso
val prefs = getSharedPreferences("myPrefs", Context.MODE_PRIVATE)
prefs.put("username", "JohnDoe")
```

### Ler Dados

Podemos criar uma extensão para ler dados das SharedPreferences.

```kotlin
fun SharedPreferences.get(key: String, default: String = ""): String {
    return getString(key, default) ?: default
}

// Uso
val username = prefs.get("username")
```

## 5. Deeplink

### Construção de Deeplinks

Podemos criar uma extensão para criar deeplinks facilmente.

```kotlin
fun String.toDeeplink(): Uri {
    return Uri.parse(this)
}

// Uso
val deeplink = "myapp://detail/123".toDeeplink()
```

### Navegação com Deeplinks

Podemos criar uma extensão para facilitar a navegação utilizando deeplinks.

```kotlin
fun Context.openDeeplink(uri: Uri) {
    startActivity(Intent(Intent.ACTION_VIEW, uri))
}

// Uso
context.openDeeplink(deeplink)
```

## 6. Concorrência

### Executar em Background

Podemos criar uma extensão para executar tarefas em uma thread de background.

```kotlin
fun runOnBackground(action: () -> Unit) {
    Executors.newSingleThreadExecutor().execute {
        action()
    }
}

// Uso
runOnBackground {
    // Tarefa a ser executada em background
}
```

### Executar no Main Thread

Podemos criar uma extensão para executar tarefas na thread principal.

```kotlin
fun runOnMain(action: () -> Unit) {
    Handler(Looper.getMainLooper()).post {
        action()
    }
}

// Uso
runOnMain {
    // Tarefa a ser executada no main thread
}
```

## 7. Http Request

### Realizar Requisição GET

Podemos criar uma extensão para realizar uma requisição GET de forma simplificada.

```kotlin
fun String.httpGet(): String {
    val url = URL(this)
    return url.readText()
}

// Uso
val response = "https://api.example.com/data".httpGet()
```

### Realizar Requisição POST

Podemos criar uma extensão para realizar uma requisição POST de forma simplificada.

```kotlin
fun String.httpPost(jsonBody: String): String {
    val url = URL(this)
    val connection = url.openConnection() as HttpURLConnection
    connection.requestMethod = "POST"
    connection.setRequestProperty("Content-Type", "application/json")
    connection.doOutput = true
    connection.outputStream.write(jsonBody.toByteArray())
    return connection.inputStream.bufferedReader().readText()
}

// Uso
val response = "https://api.example.com/data".httpPost("{\"key\":\"value\"}")
```

## 8. Json

### Parsear JSON

Podemos criar uma extensão para parsear uma string JSON em um objeto.

```kotlin
inline fun <reified T> String.fromJson(): T {
    return Gson().fromJson(this, T::class.java)
}

// Uso
val jsonString = "{\"name\":\"John\",\"age\":30}"
val person = jsonString.fromJson<Person>()
```

### Converter Objeto em JSON

Podemos criar uma extensão para converter um objeto em uma string JSON.

```kotlin
fun Any.toJson(): String {
    return Gson().toJson(this)
}

// Uso
val person = Person("John", 30)
val json = person.toJson()
```

## 9. Attribs

### Definir Margens Programaticamente

Podemos criar uma extensão para definir margens de forma programática.

```kotlin
fun View.setMargins(left: Int, top: Int, right: Int, bottom: Int) {
    val params = layoutParams as ViewGroup.MarginLayoutParams
    params.setMargins(left, top, right, bottom)
    layoutParams = params
}

// Uso
myView.setMargins(16, 16, 16, 16)
```

### Definir Padding Programaticamente

Podemos criar uma extensão para definir padding de forma programática.

```kotlin
fun View.setPaddingAll(padding: Int) {
    setPadding(padding, padding, padding, padding)
}

// Uso
myView.setPaddingAll(16)
```

Com essas extensions, você pode simplificar e otimizar o desenvolvimento de suas aplicações Android usando Kotlin.

# Prompt (Imagens)
bugdroid, ciberpunk, cabeça, múltiplos tamanhos, capa de livro
bugdroid, pixel art
Criar uma imagem com múltiplos bugdroids em estilo pixel-art sempre olhando para frente em múltiplas posições, com diferentes formatos e tamanhos, caracterizando com diferentes profissões, gerar no máximo 7 itens
Criar vários bugdroids em diferentes posições, de perfil, string
varios bugdroids, ciberpunk, cabeça,  olhos, múltiplos tamanhos, pixel-art
