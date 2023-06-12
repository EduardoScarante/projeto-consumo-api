<script></script>

<template>
  <main>
    <div class="text">
      <p class="important">
        <i>at<strong>TEMP</strong>t</i> : Tenha o Tempo em Suas Mãos
      </p>

      <p class="text">
        &nbsp Hoje, estamos entusiasmados em apresentar a vocês o site de
        previsão de tempo atTEMPt, uma plataforma online que coloca o poder das
        informações meteorológicas em suas mãos.
        <br /><br />
        &nbsp Com o atTEMPt, você terá acesso a previsões precisas, para que
        possa se preparar adequadamente e tomar decisões informadas sobre suas
        atividades diárias.<br /><br />
        &nbsp Sabemos o quão importante é ter informações confiáveis sobre o
        clima. Seja você um viajante, um entusiasta ao ar livre ou apenas alguém
        que precisa planejar suas atividades cotidianas, o atTEMPt está aqui
        para ajudá-lo a ter o controle do tempo. Então, o que torna o atTEMPt
        tão especial?
        <br />
        &nbsp &#x1f539;Confiabilidade: O atTEMPt utiliza algoritmos avançados e
        dados meteorológicos de fontes confiáveis para fornecer previsões
        precisas e confiáveis. Você terá acesso às informações mais recentes
        sobre o clima, garantindo que esteja sempre bem informado.
        <br />
        &nbsp &#x1f539;Interface Amigável: Acreditamos que a experiência do
        usuário é fundamental. Por isso, projetamos o site do atTEMPt com uma
        interface intuitiva e amigável, para que você possa navegar facilmente.
        <br />
        &nbsp &#x1f539;Personalização: Sabemos que cada pessoa tem necessidades
        e interesses diferentes quando se trata de informações meteorológicas.
        Com o atTEMPt, você pode personalizar sua busca e verificar sobre os
        aspectos do clima que são relevantes para você.
        <br />
        &nbsp &#x1f539;Recursos Adicionais: Além das previsões básicas, o
        atTEMPt também oferece recursos adicionais para melhorar sua
        experiência. Você pode visualizar imagens da cidade procurada.
        <br />
        &nbsp &#x1f539;Acessibilidade e Disponibilidade: O site do atTEMPt é
        acessível a partir de qualquer dispositivo com conexão à Internet,
        permitindo que você verifique as previsões a qualquer hora, em qualquer
        lugar.
        <br /><br />
        &nbsp Estamos comprometidos em fornecer a você informações
        meteorológicas confiáveis e úteis, para que possa tomar decisões
        informadas e planejar suas atividades com antecedência. Com o atTEMPt,
        você terá o poder de se preparar para qualquer condição climática.
        <br /><br />
      </p>
    </div>

    <div class="logo">
      <p class="important">Informações da Logo</p>

      <p>&nbsp &#x1f539;Logo completa:</p>
      <img class="logo" src="../imagens/Design sem nome.png" width="90%" />

      <p>&nbsp &#x1f539;Alguns Significados:</p>
      <a href="https://translate.google.com.br/?hl=pt-BR">
        <img src="../imagens/AttemptTRADUCAO.png" width="70%" />
        <img src="../imagens/at-tempTRADUCAO.png" width="70%" />
      </a>

      <p>&nbsp &#x1f539;Palheta de Corres:</p>
      <img class="polaroid" src="../imagens/013E9D.png" width="25%" />
      <img class="polaroid" src="../imagens/F5F7FB.png" width="25%" />
      <img class="polaroid" src="../imagens/010332.png" width="25%" />
    </div>

    <div class="api">
      <p class="important">APIs Utilizadas</p>
      <p class="text">
        <img src="../imagens/location.png" width="25px" /> API para Localização
        das Ciades do Brasil:<br /><br />
        &nbsp https://servicodados.ibge.gov.br/api/docs/localidades
      </p>

      <p class="text">
        <img src="../imagens/hot.png" width="25px" />
        API para o Clima e Temperatura:
        <br /><br />
        &nbsp https://www.visualcrossing.com/weather-api
      </p>

      <p class="text">
        <img src="../imagens/search.png" width="25px" />
        API para Pesquisa de Imagens no Google:
        <br /><br />
        &nbsp https://developers.google.com/custom-search/v1/overview?hl=pt-br
      </p>

      <p class="text">
        <img src="../imagens/love-message.png" width="25px" />
        API "Calculadora" do Amor:
        <br /><br />
        &nbsp https://rapidapi.com/ajith/api/love-calculator
      </p>
    </div>
  </main>
</template>

<style scoped>
main {
  margin-top: 50px;
  margin-left: 28%;
  margin-right: 28%;
}

.important {
  font-size: xx-large;
  text-align: center;
}

.text {
  text-align: justify;
  font-size: large;
  line-height: 1.9;
}

p {
  font-size: large;
}

.polaroid {
  margin-left: 2%;
  margin-right: 2%;
}

a > img {
  margin-left: 10%;
}

.api{
  display: flex;
  align-items: center;
}
</style>
