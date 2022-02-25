# vue-dischi

### Passaggi da fare per creazione select

- modifico header e metto la select
- nel main creo elenco generi, per spostarlo ad header prima lo mando con $emit a app.vue
- in app.vue ho l'elenco dei generi e tramite props lo passo ad header, creo la select
- all'evento di change sul select si passa a app.vue quale e' la select
- app.vue comunica la select a main che popola i dischi!
a