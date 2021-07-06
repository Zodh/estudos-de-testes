---


---

<h1 id="estudos-sobre-testes-java--springboot">Estudos sobre testes Java &amp; SpringBoot</h1>
<h3 id="felipe-c-b-santos">Felipe C B Santos</h3>
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
<p><code>@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)</code></p>
<blockquote>
<p>Anotação inserida acima de uma classe de teste que indica ao spring que os testes de repository devem ser realizados em outro banco de dados (um específico para testes), que não seja o principal de aplicação.</p>
</blockquote>
<p><code>@ActiveProfiles(“test”)</code></p>
<blockquote>
<p>Anotação inserida acima de uma classe de testes que obriga o SpringBoot a utilizar um application-test.properties, carregando as configurações de um profile específico para testes.</p>
</blockquote>
<p><code>@Test</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que um método se trata de um teste de alguma funcionalidade.</p>
</blockquote>
<p><code>@BeforeEach</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que antes de cada <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>@AfterEach</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que depois de cada <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>@BeforeAll</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que antes de todos os <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<p><code>@AfterAll</code></p>
<blockquote>
<p>Anotação inserida acima de um método para sinalizar que depois de todos os <code>@Test</code> este método deve ser executado.</p>
</blockquote>
<h2 id="dicas-para-implementação-de-testes.">Dicas para implementação de testes.</h2>
<ul>
<li>
<p>É importante que o nome do teste seja claramente descritivo independente do tamanho, de forma que o teste tenha o resultado que seu nome espera.</p>
</li>
<li>
<p>Não é mandatório, contudo, para ter uma estrutura sequencial de um teste, é recomendado que se utilize três etapas. Captura/processamento de informações necessárias para realizar o teste, execução do teste e afirmação do teste. Podendo seguir o seguinte modelo:</p>
<p><code>// arrange</code><br>
<code>[code...]</code></p>
<p><code>// act</code><br>
<code>[code...]</code></p>
<p><code>// assert</code><br>
<code>[code...]</code></p>
</li>
</ul>

