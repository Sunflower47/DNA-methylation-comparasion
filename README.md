# DNA-methylation-comparasion
Целью данного задания является изучение глобального изменения уровня CpG-метилирования ДНК при раннем эмбриональном развитии мыши и наблюдение так называемых волн деметилирования-метилирования.
Рассматриваются образцы на двух стадиях эмбрионального развития.
![DNA_methylation_reprogramming](https://github.com/user-attachments/assets/c407c178-0443-452d-9153-c0319c3af5fd)
| Accession | Стадия развития | Описание |
|-------------|-------------|-------------|
| SRR5836475 | ICM (inner cell mass)| примерно 3.5 дня после оплодотворения яйцеклетки, клетки сохраняют плюрипотентность |
| SRR3824222 | Epiblast | примерно 6.5 дней после оплодотворения яйцеклетки, начало дифференцировки клеток|

# Анализ чтений

С помощью FastQC были получены отчеты для [SRR5836475](https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/reports/SRR5836475_1_fastqc.html) и [SRR3824222](https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/reports/SRR3824222_1_fastqc.html).

Бисульфитное секвенирование меняет GC-состав, превращая неметелированный цитозин в урацил.\
На графике ниже реальное распределение GC-состава для ICM отличается от теоретического и имеет два выраженных пика: высокий, содержащий последовательности с относительно низким GC-составом (там неметилированные цитозины превратились в урацил), и меньший пик для метилированных последовательностей с более высоким GC-составом. \
Распределение GC-состава для второго образца не так сильно отличается от ожидаемого.

<table>
  <tr>
    <td colspan="2" align="center"><strong>GC-состав</strong></td>
  </tr>
  <tr>
    <td align="center"><strong>ICM (SRR5836475)</strong></td>
    <td align="center"><strong>Epiblast (SRR3824222)</strong></td>
  </tr>
  <tr>
    <td style="text-align: center;">
          <img src="https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/images/SRR5836475_1_GC_content.png" alt=""/>
    </td>
    <td style="text-align: center;">
          <img src="https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/images/SRR3824222_1_GC_content.png" alt=""/>
    </td>
</table>


# Анализ уровня метилирования
В целях экономии времени задание предполагало работу с заранее картированными ридами.\
С помощью Bismark можно получить отчет, включающий в себя общую статистику по метилированию.

| Accession |Стадия развития | Метилированные цитозины (CpG context), %| Метилированные цитозины (non-CpG context), % | Ссылка на отчет |
|-------------|-------------|-------------|-------------|-------------|
| SRR5836475 | ICM | 25.3% | 11.8% | [отчет](https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/reports/SRR5836475_bismark_report.html) |
| SRR3824222 | Epiblast | 77.1% | 17.7%| [отчет](https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/reports/SRR3824222_bismark_report.html) |

В образцах эпибласта метилирование достигает 94.8%, тогда как в образцах ICM метилированными оказываются лишь чуть больше трети цитозинов.\
На графиках ниже приведены уровни метилирования для каждой из позиции ридов. Заметные отклонения на концах, по словам авторов документации, считаются, скорее, техническим артефактами, которые обычно легко убираются триммингом.


В образцах ICM уровень метилирования для всех позиций находится в районе 25%, преобладает CpG-метилирование, как и было показано в таблице выше.
<table>
  <tr>
    <td colspan="1" align="center"><strong>M-bias plot</strong></td>
  </tr>
  <tr>
    <td align="center"><strong>ICM (SRR5836475)</strong></td>
  </tr>
  <tr>
    <td style="text-align: center;">
          <img src="https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/images/SRR5836475_bismark_M-bias_read_1.png" alt=""/>
    </td>
    <tr>
  <td style="text-align: center;">
        <img src="https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/images/SRR5836475_bismark_M-bias_read_2.png" alt=""/>
    </td>
</table>


В образцах эпибласта также преобладает CpG-метилирование, уровень которого колеблется вокруг 77%, что тоже согласуется с таблицей. Также можно отметить некоторое присутствие (порядка 1-2%) CHG- и CHH-метилирования. 

CHG- и CHH-метилирование действительно может наблюдаться во время эмбрионального периода, например, в процессах связанных с формированием нервной системы.  

<table>
  <tr>
    <td colspan="1" align="center"><strong>M-bias plot</strong></td>
  </tr>
  <tr>
    <td align="center"><strong>Epiblast (SRR3824222)</strong></td>
  </tr>
  
  
  <tr>
    <td style="text-align: center;">
          <img src="https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/images/SRR3824222_bismark_M-bias_read_1.png" alt=""/>
    </td>
    <tr>
  <td style="text-align: center;">
        <img src="https://github.com/Sunflower47/DNA-methylation-comparasion/blob/main/images/SRR3824222_bismark_M-bias_read_2.png" alt=""/>
    </td>
</table>


# Выводы

Подтвердились предположения о том, что на более раннем этапе активного деления клеток внутренней клеточной массы (inner cell mass, ICM) уровень метилирования остается низким. Эти клетки являются плюрипотентными и впоследствии могут развиваться в разные типы тканей. Уровень метилирования увеличивается по мере того, как клетки эмбриона начинают дифференцироваться. Для формирования разных типов тканей требуется активация разных наборов генов и через выборочное подавление генов метилированием организм направляет дальнейшее развитие клеток.
