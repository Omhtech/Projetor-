￼Enter file contents here
 // Importar biblioteca Tone.js
const Tone = require('tone');

// Configurar o transporte
Tone.Transport.bpm.value = 120;

// Criar sintetizador
const sintetizador = new Tone.Synth().toDestination();

// Criar melodia
const melodia = [
  ['0:0:0', 'C4', '4n'],
  ['0:1:0', 'E4', '4n'],
  ['0:2:0', 'G4', '4n'],
  ['0:3:0', 'C4', '4n'],
  ['1:0:0', 'E4', '4n'],
  ['1:1:0', 'G4', '4n'],
  ['1:2:0', 'C4', '2n'],
];

// Função para tocar a melodia
melodia.forEach(([tempo, nota, duracao]) => {
  Tone.Transport.schedule((time) => {
    sintetizador.triggerAttackRelease(nota, duracao, time);
  }, tempo);
});

// Iniciar transporte e tocar a melodia
Tone.Transport.start();
