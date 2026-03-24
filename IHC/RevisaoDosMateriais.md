# Aula 02 

## Os Principios de Donald Norman

[LINK DO ARTIGO](https://www.homemmaquina.com.br/principios-de-design-donald-norman/)

### Primeiro Principio: **Visibilidade**

**As pessoas só vão consumir e indicar um produto que elas conheçam e saibam como utilizar da forma mais eficiente possível.**
Um exemplo seria em apps de comida que precisam ter ícones que estão relacionados ao universo culinário.

### Segundo Principio: **Feedback**

**É necessário criar um mecanismo que dê ao consumidor a mensagem que o aplicativo, página ou software está trabalhando para cumprir a função que lhe foi dada.**

Sabe aqueles círculos ou mensagens de _carregando..._, é basicamente isso, precisamos dar ao usuário algum sinal que o sistema está vivo e trabalhando na tarefa que lhe foi dada.

### Terceiro Principio: **Affordance**

**O consumidor precisa olhar para a aparência de um produto e saber como utiliza-lo.**

psicologicamente isso gera um reforço positivo no usuário, este conceito está relacionado à **acessibilidade do design para o cliente**, ele precisa saber usar o site/software de forma _intuitiva_, e conseguir entender facilmente os diferenciais de seu site.

### Quarto Principio: **Mapeamento**

**Mapeamento é a relação entre controle e efeito das ações do usuário.**

Bons designs mostram ao usuário que **suas ações tem efeito**, a barra de rolagem por exemplo, mostra o qunato você já navegou na página.

### Quinto Principio: **Restrições**

**Quando criamos um design precisamos pensar nas restrições que o produto pode ter.**

Pensar em por exemplo tamanho da tela, temos que pensar em nosso design de uma forma que não conflitem com nossas restrições.

### Sexto Principio: **Consistência**

**Atender bem para atender sempre! Um bom design deve fazer com que a mesma ação gere sempre a mesma reação.**

Vamos pensar no botão de desligar, por exemplo, que em todo lugar/máquina ele tem o mesmo layout.
Temos que pensar também na identidade de marca, pois ela trás essa familiaridade e adpatação ao usuário.

## Código da Aula:
```python
import streamlit as st
import time

st.set_page_config(page_title='IHC Brabo', layout='centered')

st.title('IHC - E os princípios de norman')
st.markdows('---')

tab1, tab2 = st.tabs(['Interface do DJABO', 'Interface Massex'])

with tab1:
    st.subheader('"Tente realizar o cadastro"')
    # IHC (mapeamento memes)
    col1, col2 = st.columns(2)

    with col1:
        btn_falso_confirmar = st.button('CONFIRMAR E SALVAR', use_container_width=True)
    
    with col2:
        btn_falso_cancelar = st.button ('CANCELAR', use_container_width=True)
    
    # IHC (affordance pobre)
    entrada_misteriosa = st.text_input ('Digite Alguma Coisa: ')

    if btn_falso_confirmar:
        st.error('ERRO 0x000912: ação de bosta')
    
    # IHC (Feedback atrasado - o sistema ficará "travado")
    if btn_falso_cancelar:
        with st.empty():
            st.write('Processando...')
            time.sleep(3)
            st.warning('Processi Finalizado') # IHC (ambiguidade)

with tab2:
    st.subheader('Interface Intuitiva')

    # IHC (Affordance e Visibilidade)
    nome_usuario = st.text_input('Nome Completo: ' placeholder='EX: guga the best')

    email_usuario = st.text_input('E-mail para contato: ', placeholder='EX: naomecontate@nada.adeus)

    col_a, col_b = st.columns([1,4])

    with col_a:
        # IHC (destaque visual melhorando a consistência da interface)
        if st.button('Salvar Dados', type='primary'):

            # IHC (Validação dos dados antes de continuar)
            if nome_usuario and email_usuario:

                #IHC (feedback imediato)
                with st.spinner('Comunidando-se com o Servidor'):
                    time.sleep(1)

                # Feedback de sucesso: cor verde e mensagem clara.
                st.sucess(f'Parabéns, {nome_usuario}! Seu cadastro foi bem sucedido!')
            else:

                # Feedback de erro: explicitamente o que ele errou!
                st.error('Usuário você esqueceu de preencher o nome ou e-mail!')

                with col_b:
                    st.button('Limpar Campos', type='secondary')
```

# Aula 03

## Capítulo 2 do livro - Design Centrado no Usuário (DCU)

### 2.1 Princípios do DCU

O DCU é uma abordagem para desenvolver sistemas interativos **focados no usuário**. Levando em consideração as necessidades, limitações, contextos e etc.
A proposta do DCU é que a qualidade da interface/experiência resulta não só da funcionalidade do sistema, mas de como o **usuário percebe, utiliza, e vivência** o sistema.

#### 2.1.1 Fundamentos filosóficos e históricos 

O surgimento do DCu está profundamente relacionado ao IHC e da usabilidade especialmente nas décadas de 1980 1990. Pois nesse período os técnicos estavam percebendo que muitos sistemas bons, _"falhavam"_ por serem difíceis de usar.

Inpirado em princípios da **engenharia cognitiva** e da **psicologia do usuário**, o DCU busca alinhar os objetivos do sistema com os modelos mentais dos usuários.
Donald Norman defende que os sistemas devem ser _"Inteligentemente burros"_, ou seja simples, previsíveis e consistentes, _mesmo que seja necessário o ocultar a complexidade do código subjacente_.
O DCU Também se fundamenta em valores éticos e sociais, pra isso aborda práticas como **testes com usuários reais, feedback contínuo e melhoria interativa**.

#### 2.1.2 Definições normativas: ISO 9241-210

A ISO 9241-210 Define o DCU como: Uma abordagem ao design de sistemas interativos que visa tornar os sistemas _utilizáveis_, centrando-se na utilização do sistema, na compreensão e no contexto do usuário, com uma **participação ativa** do usuário ao longo de todo o processo de projeto e desenvolvimento.

Segundo a norma, os **princípios fundamentais** do DCU são:

* O design baseado na compreensão explícita dos usuários tarefas e ambientes. Isso significa que o projeto de interface começa com estudo sistemático dos usuários reais;
* Os usuários estão envolvidos ativamente durante todo o processo de design e desenvolvimento. Usuários reais são consultados desde a fase de concepção até o lançamento e manutenção;
* O design e impulsionado e refinado por meio da avaliação centrada no usuário. Prototipagem e testes com usuários devem ser realizados em ciclos iterativos.
* O processo é iterativo. O DCU prevê ciclos de design, prototipagem, teste e reformulação. A interação com os usuários não é pontual, mas contínua.
* O design atende a toda a experiência do usuário. Vai além da interface visual ou da funcionalidade, considera emoções, expectativas e etc
* A equipe de projeto é multidisciplinar. O sucesso do DCU depende da colaboração entre designers, engenheiros e etc.

#### 2.1.3 O papel do usuário no DCU

O ponto central do DCU é a valorização do usuário como **especialista de sua própria experiência**. Isso não quer dizer que o usuário irá tomar as decisões de design, mas sim que sua perspectiva deve ser respeitada, investigada e integrada ao projeto.
O DCU valoriza também a diversidade de perfis, reconhecendo que diferentes pessoas podem interagir de formas distintas com o sistema.

O _design universal_ se baseia em sete princípios estabelecidos por _ron mace e equipe_:
* Uso equitativo;
* Flexibilidade no uso;
* Simples e intuitivo;
* Informação perceptível;
* Tolerância a erros;
* Baixo esforço físico;
* Tamanho e espaço apropriados;

