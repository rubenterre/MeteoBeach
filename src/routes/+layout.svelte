<script>

</script>
<header class="header">
    <nav class="header__nav">
        <img src="MeteoBeach_logo.svg" alt="Logo de MeteoBeach Sanxenxo" class="header__logo">
    </nav>
</header>

<slot></slot>

<style>


@font-face {
		font-family: Montserrat-Regular;
		src: url(fonts/Montserrat-Regular.otf);
	}

@font-face {
		font-family: Montserrar-SemiBold;
		src: url(fonts/Montserrat-SemiBold.otf);
	}

@font-face {
		font-family: MontserrarAlternates-Regular;
		src: url(fonts/MontserratAlternates-Regular.ttf);
	}

:root{
    --color-principal: #11292D;
	--color-secundario: #01A7B5;
	--color-fondo: #283E41;
	--color-secundario-matiz: #7F8080;
	--fuente-principal: Montserrat-Regular;
	--fuente-secundaria: MontserrarAlternates-Regular;
	--fuente-terciaria: Montserrat-SemiBold;
}

:global(*) {
  margin: 0;
  padding: 0;
  outline: 0;
  box-sizing: border-box;
}

:global(html){
    background-color: var(--color-fondo);
 background: url(fondo.jpeg);
 background-size: cover;
 background-position: center;
 background-repeat: no-repeat;
 height: 100vh;
}

:global(body) {
 background: linear-gradient(180deg, rgba(17,41,45,0.75) 0%, rgba(1,167,181,0.63) 100%);
 color: white;
 height: 100vh;
 -webkit-font-smoothing: antialiased;
}

:global(body, input, button) {
 font-size: 14px ;
 font-family: var(--fuente-principal);
}

:global(button) {
 cursor: pointer;
}

.header{
    background-color: var(--color-principal);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px 0px;
}

.header__logo{
    width: 98px;
}

</style>