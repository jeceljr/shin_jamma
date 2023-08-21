# Interface shin_jamma para projetos com FPGA

Converter um projeto Verilog que está funcionando numa placa com FPGA específica
para uma placa diferente pode ser bem trabalhoso. Uma solução é definir uma
interface padrão e implementar um componente de adaptação par cada placa ligando
o projeto do usuário às interfaces reais implementadas por aquela placa
particular.

Isso é no mesmo espírito que a interface padrão JAMMA (Japanese Arcade Machine Manufacturers Association) para ligar gabinetes às placas dos jogos, que é a
razão pela qual Mario Gazziro sugeriu o nome shin (novo) JAMMA. O conector JAMMA
de 56 pinos inclue alimentação, vídeo e falante analógicos e também interfaces
para botões enquanto este padrão tem apenas sinais digitais, mas a funcionalidade
é semelhante.

## Placas Atuais

## Placas Planejadas

- Terasic DE0
- Terasic DE0-CV
- Terasic DE0-Lite
- Terasic DE10-Nano
- Terasic DE2-70
- Terasic DE2-115
- SiPeed Tango Nano 20K
- Xess XSA100
- Xilinx ML401
