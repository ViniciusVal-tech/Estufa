#### Igor, Gabriel, Raphaela e Vinicius
## Introdução 

 O cultivo de plantas ornamentais tem se destacado nos últimos anos, especialmente com o aumento da procura por plantas em vasos. Muitas pessoas encontraram na jardinagem uma forma de melhorar o bem-estar e aliviar os efeitos do isolamento, tornando esse mercado cada vez mais promissor.  
 As estufas oferecem o ambiente ideal para o cultivo de plantas ornamentais, principalmente as suculentas. Essas plantas são resistentes, exigem pouca manutenção e se adaptam bem a ambientes controlados. Elas possuem um metabolismo que economiza água, o que as torna perfeitas para produção em larga escala.  
 A propagação das suculentas, geralmente feita por estaquia, é eficiente, de baixo custo e acelera o retorno financeiro. As estufas possibilitam o controle de temperatura, umidade e luz, protegendo as plantas contra pragas e doenças e favorecendo um crescimento uniforme, mesmo em regiões com clima mais rigoroso.  
 Além disso, o uso de substratos apropriados, fertilizantes de liberação lenta e sistemas de irrigação econômicos aumenta a produtividade. Outro benefício é o controle fitossanitário mais rigoroso, com técnicas que garantem plantas livres de vírus, essenciais para comercialização e exportação. Do ponto de vista econômico, investir em uma estufa pode ser vantajoso, desde que haja planejamento e produção em volume adequado.   Os indicadores financeiros demonstram que esse tipo de projeto é viável e pode gerar retorno em poucos anos.  
Montar uma estufa de plantas ornamentais é uma ótima forma de garantir um ambiente protegido e ideal para o crescimento saudável das plantas. As suculentas se desenvolvem melhor nesse tipo de espaço, com luz, calor e umidade controlados. Com esses cuidados, elas crescem mais fortes, bonitas e livres de doenças.  
Estaquia é um método de reprodução de plantas onde se utiliza partes como galhos ou folhas para gerar novas mudas. É uma forma rápida e eficiente de clonar a planta-mãe.
Fitossanitário se refere aos cuidados para proteger as plantas contra pragas e doenças. Garante a saúde das plantas durante o cultivo e comercialização.  

![Montagem](Fotos/Montagem.png)

```C++
int valorLDR;
int valorLUZ;
int cancel = 0;

void setup()
{
  Serial.begin(9600);
  pinMode(A0, INPUT);
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(6, OUTPUT);
}

void loop()
{
  valorLDR = analogRead(A0);
  valorLUZ = map(valorLDR,2,404,0,900);
  
  if (valorLUZ >= 720 && cancel != 3){								//VERMELHO
  	digitalWrite(9, HIGH); 
    digitalWrite(10, LOW);
    digitalWrite(11, LOW);
    
    emitirApitos(3);
    cancel = 3;
    
  } else if (valorLUZ >= 450 && valorLUZ < 720 && cancel != 2){	// AMARELO
  	digitalWrite(10, HIGH);
    digitalWrite(9, LOW);
    digitalWrite(11, LOW);
    
    emitirApitos(2);
    cancel = 2;
    
  } else if (valorLUZ < 450 && cancel != 1){											// VERDE
	digitalWrite(11, HIGH);
    digitalWrite(9, LOW);
    digitalWrite(10, LOW);
    
    emitirApitos(1);
    cancel = 1;
  }
  
  Serial.print("LDR: ");
  Serial.println(valorLDR);
  
  Serial.print("Luz: ");
  Serial.println(valorLUZ); 
}
  
void emitirApitos(int quantidade) {
  for (int i = 0; i < quantidade; i++) {
    digitalWrite(6, HIGH);
    delay(100);
    digitalWrite(6, LOW);
    delay(200);
  }
}
```
### Referências
http://www.iea.sp.gov.br/ftpiea/ie/1995/tec4-0895.pdf

https://www.researchgate.net/profile/Margarida-Teixeira-Santos/publication/269112725_Detecao_de_Virus_em_estufas_de_plantas_ornamentais_incluindo_virus_detetados_pela_primeira_vez_em_Portugal/links/5481fd9a0cf2e5f7ceabef3f/Detecao-de-Virus-em-estufas-de-plantas-ornamentais-incluindo-virus-detetados-pela-primeira-vez-em-Portugal.pdf

https://docs.ufpr.br/~marianakleina/TCC_AndreDelForno.pdf
