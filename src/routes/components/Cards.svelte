<script>
  export let waterTemperature;
  export let airTemperature;
  export let uvIndex;

</script>

<div class="card">
    <div class="card__fondo">
        <div class="card__icon">
            <img class="card__img" src="icons/weather/01d.png" width="80px" alt="Icono del tiempo">
        </div>
        <div class="card__detalle">
            <div class="card__titulo">
                <h3 class="card__h3">
                    Praia de Areas
                </h3>
                <p class="card__p--strong">
                    31 agosto 2024
                </p>
            </div>
            <div class="card__datos">
                <div class="card__pill">
                    <h4 class="card__h4">
                        {airTemperature}
                    </h4>
                    <p class="card__p">
                        TEMP
                    </p>
                    <hr class="card__hr">
                </div>
                <div class="card__pill">
                    <h4 class="card__h4">
                        22º
                    </h4>
                    <p class="card__p">
                        MIN
                    </p>
                    <hr class="card__hr">
                </div>
                <div class="card__pill">
                    <h4 class="card__h4">
                        {waterTemperature}
                    </h4>
                    <p class="card__p">
                        AGUA
                    </p>
                    <hr class="card__hr">
                </div>
                <div class="card__pill">
                    <h4 class="card__h4">
                        {uvIndex}
                    </h4>
                    <p class="card__p">
                        UV
                    </p>
                    <hr class="card__hr">
                </div>
            </div>
        </div>
        <div class="card__forma">
            <img class="card__flecha" src="forma_card.svg" alt="forma">
        </div>
    </div>
</div>

<style>

.card{
    background: var(--color-secundario);
    border-radius: 8px;
    width: 100%;
    height: 129px;
}

.card__fondo{
    background: var(--color-principal);
    display: grid;
    grid-template-columns: 1fr 3fr .5fr;
    justify-content: center;
    align-items: center;
    height: 100%;
    border-radius: 8px;
}

.card__icon{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 20px;
}

.card__titulo{
    padding-bottom: 20px;
}

.card__detalle{
    margin-left: 20px;
}

.card__forma{
    display: flex;
    justify-content: end;
}

.card__datos{
    display: flex;
    justify-content: space-between;
    gap: 10px;
}

.card__pill{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.card__h4{
    font-family: var(--fuente-principal);
 font-size: 1.2rem;
 color: white;
 font-weight: 300;
}

.card__p{
 font-family: var(--fuente-principal);
 font-size: .8rem;
 color: white;
 font-weight: 700;
}

.card__hr{
    width: 100%;
}
</style>