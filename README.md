# ARDUINO-CONTROLADOR-MIDI-SEIS-POTENCIOMETROS
ARDUINO CONTROLADOR MIDI CON SEIS POTENCIOMETROS 


//-----------------------------------------------------------------------1.MIXER 6 POTS MIDI ABLETON, INICIO-------------------------------------------------------------------------------
int v0 = 0;
int v0_ = 0;
int v1 = 0;
int v1_ = 0;
int v2 = 0;
int v2_ = 0;
int v3 = 0;
int v3_ = 0;
int v4 = 0;
int v4_ = 0;
int v5 = 0;
int v5_ = 0;
int threshold = 2;
int int_to_midi_ratio = 1024 / 128;

void SendMidiToSerial (unsigned char word0, unsigned char word1, unsigned char word2) {
  Serial.write(word0);
  Serial.write(word1);
  Serial.write(word2);
}
//-----------------------------------------------------------------1.MIXER 6 POTS MIDI ABLETON, FINAL-----------------------------------------------------------------------------------------


void setup () {

  //---------------------------------------------------------------1.MIXER 6 POTS MIDI ABLETON, VOID SETUP INICIO---------------------------------------------------------------------------
  //Serial.begin(31250); // HIDUINO; FINAL, OJO QUITAR DIAGONALES PARA HABILITAR, ESTA OPCION O LA DE ABAJO.
  Serial.begin(57600); // 1ER. PRUEBA O TEST
  //Serial.begin(11)

}
//----------------------------------------------------------------1.MIXER 6 POTS, MIDI ABLETON, VOID SETUP FINAL------------------------------------------------------------------------------


void loop () {

  //------------------------------------------------------------1.MIXER 6 POTS, MIDI ABLETON, VOID LOOP, INICIO------------------------------------------------------------------------------
  v0 = analogRead(0) / int_to_midi_ratio;
  v1 = analogRead(1) / int_to_midi_ratio;
  v2 = analogRead(2) / int_to_midi_ratio;
  v3 = analogRead(3) / int_to_midi_ratio;
  v4 = analogRead(4) / int_to_midi_ratio;
  v5 = analogRead(5) / int_to_midi_ratio;
  
  if (v0 - v0_ >= threshold || v0_ - v0 >= threshold) {
    v0_ = v0;
    SendMidiToSerial(176, 42, v0);
  }
  
  if (v1 - v1_ >= threshold || v1_ - v1 >= threshold) {
    v1_ = v1;
    SendMidiToSerial(176, 43, v1);
  }

  if (v2 - v2_ >= threshold || v2_ - v2 >= threshold) {
    v2_ = v2;
    SendMidiToSerial(176, 44, v2);
  }

    if (v3 - v3_ >= threshold || v3_ - v3 >= threshold) {
    v3_ = v3;
    SendMidiToSerial(176, 45, v3);
  }
  
  if (v4 - v4_ >= threshold || v4_ - v4 >= threshold) {
    v4_ = v4;
    SendMidiToSerial(176, 46, v4);
  }

  if (v5 - v5_ >= threshold || v5_ - v5 >= threshold) {
    v5_ = v5;
    SendMidiToSerial(176, 47, v5);
  }
  
}

//------------------------------------------------------------1.MIXER 6 POTS, MIDI ABLETON, VOID LOOP, FINAL------------------------------------------------------------------------------
