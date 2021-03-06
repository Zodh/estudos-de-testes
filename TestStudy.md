---


---

<h1 id="estudos-sobre-testes-java--springboot">Estudos sobre testes Java &amp; SpringBoot</h1>
<h4 id="felipe-c-b-santos">Felipe C B Santos</h4>
<p>Arquivo criado para facilitar os estudos relativos a testes.</p>
<p><a href="https://stackoverflow.com/questions/55276555/when-to-use-runwith-and-when-extendwith">When to use @RunWith and when @ExtendWith</a></p>
<p>Se você estiver usando uma versão mais antiga que a 5 do Junit, então você deve utilizar:<br>
<code>@RunWith(SpringRunner.class)</code> ou <code>@RunWith(MockitoJUnitRunner.class)</code> etc.</p>
<p>Mas se você estiver usando a versão 5 do Junit então você deve utilizar:  <code>@ExtendWith(SpringExtension.class)</code> ou <code>@ExtendWith(MockitoExtension.class)</code> etc.</p>
<p><code>@SpringBootTest</code></p>
<blockquote>
<p>Anotação genérica inserida acima de uma classe de testes para sinalizar que a classe é um teste/um conjunto de teste(s) de alguma(s) funcionalidade(s) desenvolvida(s) com SpringBoot. Serve para iniciar os <code>@Beans</code> da aplicação e o servidor.</p>
</blockquote>
<p><code>@DataJpaTest</code></p>
<blockquote>
<p>Funciona de forma semelhante ao <code>@SpringBootTest</code>, contudo, é específico para teste de interfaces Repository. A diferença, é que já provê algumas coisas pro caso de repository, como: todos os métodos de teste já terão um controle de transação, injeção de EntityManagers específicos para testes e tratamentos específicos para teste de repository.</p>
</blockquote>
<p><code>@WebMvcTest</code></p>
<blockquote>
<p>Funciona de forma semelhante ao <code>@SpringBootTest</code>, contudo, é específico para teste da camada de Controller. A diferença, é que já provê algumas coisas pro caso de controllers, como: controllers, rest controllers, controller advice e tudo relacionada à camada MVC do projeto. Mas é importante sinalizar que esta anotação não inicializa as camadas de service/processamento da aplicação.</p>
</blockquote>
<p><code>@AutoConfigureMockMvc</code></p>
<blockquote>
<p>Anotação acima da classe que configura o mockMvc, que possibilita disparar requests nos testes de controllers. É carregado com todas as camadas). Caso a anotação <code>@WebMvcTest</code> esteja assinada, esta se torna obsoleta.</p>
</blockquote>
<p><code>@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)</code></p>
<blockquote>
<p>Anotação inserida acima de uma classe de teste que indica ao spring que os testes de repository devem ser realizados em outro banco de dados (um específico para testes), que não seja o principal de aplicação.</p>
</blockquote>
<p><code>@ActiveProfiles("test")</code></p>
<blockquote>
<p>Anotação inserida acima de uma classe de testes que obriga o SpringBoot a utilizar um application-test.properties, carregando as configurações de um profile específico para testes.</p>
</blockquote>
<p><code>@Test</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que um método se trata de um teste de alguma funcionalidade.</p>
</blockquote>
<p><code>@BeforeEach</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que <strong>antes de cada</strong> <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>@AfterEach</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que <strong>depois de cada</strong> <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>@BeforeAll</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que <strong>antes de todos</strong> os <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>@AfterAll</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que <strong>depois de todos</strong> os <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>MockMvc</code></p>
<blockquote>
<p>Classe capaz de disparar requisições http: <code>mockMvc.perform(MockMvcRequestBuilders .[protocoloHttp](uri) .content(conteudoParametroDaRequisicao) .contentType(MediaType.APPLICATION_JSON)</code><br>
<strong>.andExpect(MockMvcResultMatchers</strong><br>
<strong>.status()</strong><br>
<strong>.is(400))</strong><br>
(estas linhas em negrito se assemelham a um assert)</p>
</blockquote>
<h2 id="dicas">Dicas</h2>
<ul>
<li>
<p>O nome do método deve ser nos modelos: <a href="https://martinfowler.com/bliki/GivenWhenThen.html">GivenWhenThen</a> ou nomeDoMetodoQueEstaSendoTestado.</p>
</li>
<li>
<p>Não é mandatório (mas na HST é), contudo, para ter uma estrutura sequencial de um teste, é recomendado que se utilize três etapas. Captura/processamento de informações necessárias para realizar o teste, execução do teste e afirmação do teste. Podendo seguir o seguinte modelo:</p>
<p><code>// arrange - organizar o que será testado - given</code><br>
<code>[code...]</code></p>
<p><code>// act - execução - when</code><br>
<code>[code...]</code></p>
<p><code>// assert - validação - then</code><br>
<code>[code...]</code></p>
</li>
<li>
<p>Um teste unitário é um Box Test. O teste deve ser executado no seu computador e ter capacidade para ser executado em qualquer local.</p>
</li>
<li>
<p>Stubs: o seu computador deve prover uma base/webservice. Um mock do serviço.</p>
</li>
</ul>
<h3 id="mock">Mock</h3>
<blockquote>
<p>Mock se trata de uma simulação de comportamento de determinada classe.</p>
</blockquote>
<ul>
<li><a href="https://stackoverflow.com/questions/16467685/difference-between-mock-and-injectmocks">Diferença entre @InjectMocks e @Mock</a></li>
<li><code>@InjectMocks</code>: um manager com diversos objetos</li>
<li><code>@Mock</code>: um objeto.</li>
</ul>
<h3 id="jacoco">JaCoCo</h3>
<blockquote>
<p>O <strong>JaCoCo</strong> se trata de um plugin maven que funciona como um “gerador de relatórios de cobertura de testes em relação ao código para projetos java”.</p>
</blockquote>
<pre><code>Como abrir o relatório do JaCoCo? 
target --&gt; site --&gt; jacoco --&gt; index --&gt; open in default
</code></pre>
<p><a href="https://www.baeldung.com/jacoco">Estudo completo - Baeldung</a></p>

