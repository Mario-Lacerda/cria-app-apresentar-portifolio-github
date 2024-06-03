# Desafio - Criando um App para Apresentar seu Portfólio do GitHub


### Projeto: App para Apresentar seu Portfólio do GitHub



Este projeto tem como objetivo criar um aplicativo Android completo que permita que você apresente seu portfólio do GitHub de maneira elegante e simplificada. O aplicativo será construído usando o Android Studio, a biblioteca de componentes Jetpack e a API do GitHub.



#### **Estrutura do Projeto**

O projeto será estruturado em vários módulos, incluindo:

- Módulo `app`: Contém a lógica principal do aplicativo, como navegação e gerenciamento de dados.
- Módulo `github`: Contém a lógica para acessar e exibir informações do seu portfólio do GitHub.
- Módulo `core`: Contém classes e utilitários comuns usados por outros módulos.



#### **Recursos do Aplicativo**

O aplicativo terá os seguintes recursos:

- **Tela de Login:** Permite que você faça login com sua conta do GitHub.
- **Tela de Portfólio:** Exibe uma lista de seus repositórios do GitHub, organizados por estrelas ou atualizações recentes.
- **Tela de Detalhes do Repositório:** Exibe informações detalhadas sobre um repositório específico, incluindo descrição, colaboradores, commits recentes e muito mais.
- **Tela de Pesquisa:** Permite pesquisar repositórios por nome, descrição ou linguagem.
- **Tela de Perfil:** Exibe informações sobre seu perfil do GitHub, incluindo nome de usuário, biografia e estatísticas.



#### **Código do Projeto**

#### **MainActivity.kt**

kotlin

```kotlin
package com.example.githubportfolio

import android.content.Intent
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        loginButton.setOnClickListener {
            val intent = Intent(this, PortfolioActivity::class.java)
            startActivity(intent)
        }
    }
}
```



#### **PortfolioActivity.kt**

kotlin

```kotlin
package com.example.githubportfolio

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView
import kotlinx.android.synthetic.main.activity_portfolio.*

class PortfolioActivity : AppCompatActivity() {

    private val repositories = mutableListOf<Repository>()
    private val adapter = RepositoryAdapter(repositories)

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_portfolio)

        recyclerView.layoutManager = LinearLayoutManager(this)
        recyclerView.adapter = adapter

        // Carregar repositórios do GitHub aqui
    }
}
```



#### **RepositoryAdapter.kt**

kotlin

```kotlin
package com.example.githubportfolio

import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView
import kotlinx.android.synthetic.main.item_repository.view.*

class RepositoryAdapter(private val repositories: MutableList<Repository>) : RecyclerView.Adapter<RepositoryAdapter.ViewHolder>() {

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view = LayoutInflater.from(parent.context).inflate(R.layout.item_repository, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val repository = repositories[position]

        holder.nameTextView.text = repository.name
        holder.descriptionTextView.text = repository.description
    }

    override fun getItemCount(): Int = repositories.size

    class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        val nameTextView: TextView = itemView.nameTextView
        val descriptionTextView: TextView = itemView.descriptionTextView
    }
}
```



### **Conclusão**

Este projeto fornece um modelo completo para criar um aplicativo Android que permita que você apresente seu portfólio do GitHub de maneira elegante e simplificada. O aplicativo pode ser personalizado para atender às suas necessidades específicas, adicionando recursos adicionais, como notificações de novos commits ou a capacidade de compartilhar seus repositórios com outras pessoas.







## Descrição do Desafio.

Crie um App Android para apresentar seu portfólio de projetos do GitHub de maneira elegante e simplificada. Nesse contexto, você passará por todo o processo de desenvolvimento usando o Kotlin, uma das linguagens de programação de maior ascensão nos últimos anos. 

### Novas Tecnologias como:

- [API de REST do GitHub](https://docs.github.com/pt/rest)

- [SampleData](https://medium.com/android-news/android-tools-attributes-listitem-sample-data-rocks-bbf49aaa9f07)
- [Material Chip](https://material.io/components/chips/android#using-chips)

- [Glide](https://github.com/bumptech/glide)
- [Picasso](https://square.github.io/picasso/)
