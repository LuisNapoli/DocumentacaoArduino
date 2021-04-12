### DocumentacaoArduino

# Semáforo de veículos e semáforo para pedestre. 🚦

Esse projeto foi baseado em um semáforo com um botão para pedestres, caso um pedestre queira atravessar a rua, ele simplesmente aperta o botão e isso fará com que o semáforo de veiculos mude do verde para o amarelo e em seguida para o vermelho. Depois disso, o semáforo de pedestres vai do vermelho para o verde, dando tempo suficiente para que o pedestre consiga atravessar a rua e assim, o semáforo de pedestres volta ao vermelho e o de veículos volta ao verde.


## Material necessário:

* 2x leds vermelhos 🔴
* 1x led amarelo 🟡
* 2x leds verdes 🟢

* 1x botão 

* 5x resistores 220 ohms
* 1x resistor 10 kohms

* 1x ardunino

* 1x protoboard

*O arduino e todos os componentes foram simulados em https://www.tinkercad.com/*


## Como foi feito:

Os leds foram separados no protoboard, 1x vermelho, 1x amarelo e 1x verde, para o semáforo de veículos e, 1x vermelho e  1x verde, para o semáforo de pedestres.

Cada led recebeu um resistor de 200 ohms em seu catodo, ligadas no GND. Já o anodo foi conectado nas portas do arduino. Foram usadas as portas:
	
   #### Semaforo Veiculo
	Led Vermelho: Porta ~11
	Led Amarelo: Porta 10
	Led Verde: Porta ~9
   #### Semaforo Pedestre	
	Led Vermelho: Porta 4
	Led Verde: Porta ~3


## Circuito do botão:

O resistor de 10kohms foi conectado no terminal 1a do botão até o 5v do arduino. 
O terminal 2b foi conectado ao GND
O terminal 2a foi conectado a porta ~5

![botao](https://i.imgur.com/5l5uh5q.png) 

## Usando o projeto e explicando seu funcionamento.

Para ver o projeto funcionando é bem simples, ligar na eneria e apertar o botão.

![arduino](https://i.imgur.com/Ch8nHEP.gif)

O led verde de veiculo vai acender junto com o led vermelho do pedestre. 
Com o botão sendo pressionado, o semáforo de veiculo vai mudar para o amarelo e logo após para o vermelho, só depois que o semaforo de veiculo acender o vermelho que o semaforo de pedestre irá mudar para o verde. 
Nisso, exestira um atraso para que seja o tempo para a travessia do pedestre e logo após o semaforo de pedestre ficar vermelho que o semaforo de veiculos ira para o verde.

## Código: 
``` // Configuração dos leds com o arduino
void setup()
{
  pinMode(4, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(5, INPUT);
  pinMode(10, OUTPUT);
}

// Configuração do tempo dos leds
void loop()
{
  // Acende o VERDEveiculo
  digitalWrite(4, HIGH);
  digitalWrite(3, LOW);
  delay(1000); //Espera 1000 millisecond(s)
  digitalWrite(11, LOW);
  digitalWrite(9, HIGH);
  delay(4000); // Espera 4000 millisecond(s)
  //Condicao do botao
  if (digitalRead(5) == 0) {
    // Acende o AMARELOveiculo
    digitalWrite(9, LOW);
    digitalWrite(10, HIGH);
    delay(2000); // Espera 2000 millisecond(s)
    // Acende o VERMELHOveiculo
    digitalWrite(10, LOW);
    digitalWrite(11, HIGH);
    digitalWrite(4, LOW);
    digitalWrite(3, HIGH);
    delay(3000); // Espera 3000 millisecond(s)
  }
}
```



