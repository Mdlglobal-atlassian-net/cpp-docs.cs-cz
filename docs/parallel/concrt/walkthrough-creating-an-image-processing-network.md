---
title: "Návod: Vytvoření sítě pro zpracování obrázků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b709179cb5bc0fefa3f342374c792656fa1e934
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Návod: Vytvoření sítě pro zpracování obrázků
Tento dokument ukazuje, jak vytvořit síť asynchronní bloky zpráv provádějící zpracování obrázků.  
  
 Síť určení operací, které k plnění bitovou kopii na základě jeho vlastnosti. Tento příklad používá *toku dat* modelu na trasy Image přes síť. V modelu toku dat nezávislé komponenty programu vzájemnou komunikaci odesláním zprávy. Když součást obdrží zprávu, může provedení několika akcí a poté předat další komponentou výsledek této akce. Výsledky porovnejte s *řízení toku* modelu, ve kterém aplikace využívá řídicí struktury, například, podmíněné příkazy, smyčky a tak dále, řídit pořadí operací v programu.  
  
 Vytvoří síť, která je založena na toku dat *kanálu* úloh. Každá fáze v kanálu souběžně provede součástí celkového úlohy. Analogie k tomuto je sestavení pro automobilů výrobní. Při každém vehicle průchodu řádku sestavení, jedné stanici sestaví rámečku, jiné nainstaluje modul a tak dále. Povolením více vozidel pro sestavení současně řádku sestavení poskytuje lepší propustnost než ty dokončení vozidel jeden najednou.  
  
## <a name="prerequisites"></a>Požadavky  
 Přečtěte si následující dokumenty, než začnete Tento názorný postup:  
  
-   [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
-   [Postupy: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
  
 Doporučujeme taky, že chápete základní informace o [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] před spuštěním tohoto průvodce.  
  
##  <a name="top"></a>Oddíly  
 Tento názorný postup obsahuje následující části:  
  
-   [Definování zpracování funkce obrázku](#functionality)  
  
-   [Vytvoření sítě pro zpracování bitové kopie](#network)  
  
-   [Úplný příklad](#complete)  
  
##  <a name="functionality"></a>Definování zpracování funkce obrázku  
 Tato část uvádí podpory funkce, které používá síť zpracování bitové kopie pro práci s obrázky, které se načítají z disku.  
  
 Následující funkce `GetRGB` a `MakeColor`, extrahovat a kombinace jednotlivých součástí dané barvy, v uvedeném pořadí.  
  
 [!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]  
  

 Následující funkce `ProcessImage`, volání danou [std::function](../../standard-library/function-class.md) objektu k transformaci hodnoty barvy každý pixelů v [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [rastrový obrázek](https://msdn.microsoft.com/library/ms534420.aspx) objektu. `ProcessImage` Využívá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus pro každý řádek rastrový obrázek paralelní zpracování.  

  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]  
  
 Následující funkce `Grayscale`, `Sepiatone`, `ColorMask`, a `Darken`, volání `ProcessImage` funkce k transformaci hodnoty barvy každý pixelů v `Bitmap` objektu. Každá z těchto funkcí výrazu lambda používá k definování barva transformace jeden pixel.  
  
 [!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]  
  
 Následující funkce `GetColorDominance`, také voláním `ProcessImage` funkce. Však místo změně hodnoty nebo jednotlivé barvy, tato funkce využívá [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) objekty k výpočtu, zda součást red, zelenou nebo modrou barvu dominuje bitovou kopii.  
  
 [!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]  
  
 Následující funkce `GetEncoderClsid`, načte identifikátor třídy pro daný typ MIME pro kodér. Aplikace používá tuto funkci pro načtení modulu encoder rastrového obrázku.  
  
 [!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="network"></a>Vytvoření sítě pro zpracování bitové kopie  
 Tato část popisuje, jak vytvořit síť asynchronní bloky zpráv provádějící zpracování obrázků na každý [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] bitové kopie (.jpg) v daném adresáři. Síť provede následující operace zpracování obrázků:  
  
1.  Pro všechny image, která je vytvořená tní převeďte na ve stupních šedi.  
  
2.  Pro žádný obrázek, který má red jako dominantní barvu odebrat zelené a modré součásti a poté ji ztmavení.  
  
3.  Pro další bitovou kopii použijte sépiový tónování.  
  
 Síť se vztahuje pouze první zpracování obrázků operaci, která odpovídá jednomu z těchto podmínek. Například pokud bitovou kopii je vytvořená tní a má red jako její dominantní barvy, bitovou kopii je pouze převedeno na ve stupních šedi.  
  
 Po síti provede každou operaci zpracování obrázků, uloží jako soubor rastrový obrázek (BMP) bitovou kopii disku.  
  
 Následující kroky ukazují, jak vytvořit funkci, která implementuje sítě pro zpracování této bitové kopie a použije tuto síť ke každému [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] bitové kopie v daném adresáři.  
  
#### <a name="to-create-the-image-processing-network"></a>Vytvoření sítě zpracování obrázků  
  
1.  Vytvoří funkci, `ProcessImages`, který přebírá název adresáře na disku.  
  
     [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]  
  
2.  V `ProcessImages` fungovat, vytvořte `countdown_event` proměnné. `countdown_event` Je například znázorněn dále v tomto návodu.  
  
     [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]  
  
3.  Vytvoření [std::map](../../standard-library/map-class.md) objekt, který přidruží `Bitmap` objekt s jeho původní název souboru.  
  
     [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]  
  
4.  Přidejte následující kód k definování členů sítě pro zpracování obrázků.  
  
     [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]  
  
5.  Přidejte následující kód k připojení k síti.  
  
     [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]  
  
6.  Přidejte následující kód k odeslání do head sítě úplnou cestu jednotlivých [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] soubor v adresáři.  
  
     [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]  
  
7.  Počkejte `countdown_event` proměnnou na nulu.  
  
     [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]  
  
 Následující tabulka popisuje členy sítě.  
  
|Člen|Popis|  
|------------|-----------------|  
|`load_bitmap`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) objekt, který načítá `Bitmap` objektu z disku a přidá položku do `map` objekt, který chcete přidružit k jeho původní název souboru obrázku.|  
|`loaded_bitmaps`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který odesílá načíst Image pro filtry zpracování obrázků.|  
|`grayscale`|A `transformer` objekt, který převádí bitové kopie, které jsou vytvořeny pomocí tní k ve stupních šedi. Metadata bitové kopie se používá k určení jeho autora.|  
|`colormask`|A `transformer` objekt, který odebere komponenty zelenou a modrou barvu z bitové kopie, které mají red jako dominantní barvu.|  
|`darken`|A `transformer` objekt, který ztmaví bitové kopie, které mají red jako dominantní barvu.|  
|`sepiatone`|A `transformer` objekt, který se vztahuje sépiový tónování bitové kopie, které nejsou autorem tní a nejsou převážně red.|  
|`save_bitmap`|A `transformer` objekt, který uloží zpracování `image` na disk jako rastrový obrázek. `save_bitmap`načte původní název souboru z `map` objektu a jeho příponu názvu souboru se změní na .bmp.|  
|`delete_bitmap`|A `transformer` objekt, který uvolní paměť pro bitové kopie.|  
|`decrement`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) objekt, který funguje jako terminálu uzlu v síti. Se snižuje `countdown_event` objektu k hlavní aplikaci signál, že byla zpracována bitovou kopii.|  
  
 `loaded_bitmaps` Zpráva vyrovnávací paměť je důležité, protože jako `unbounded_buffer` objektu, nabízí `Bitmap` objekty do několika příjemců. Pokud cílový blok přijme `Bitmap` objekt, `unbounded_buffer` objektu, která nenabízí `Bitmap` objekt, který má jiné cíle. Proto pořadí, ve kterém můžete propojit objekty ke `unbounded_buffer` objektu je důležité. `grayscale`, `colormask`, A `sepiatone` zpráva bloky každý pomocí filtru tak, aby přijímal pouze určité `Bitmap` objekty. `decrement` Zpráva vyrovnávací paměť je důležité cíl `loaded_bitmaps` zprávy vyrovnávací paměti, protože všechny přijímá `Bitmap` objekty, které jsou odmítnut další zprávy vyrovnávací paměti. `unbounded_buffer` Objektu je potřeba rozšířit zprávy v pořadí. Proto `unbounded_buffer` objekt zablokuje, dokud se nový cílový blok se odkazuje a přijímá zprávy, pokud žádný aktuální cílový blok přijímá zprávy.  
  
 Pokud vaše aplikace vyžaduje více zprávy blokuje proces zprávu, ale právě jednu zprávu blok, který nejprve přijímá zprávy, můžete použít jiný typ bloku zpráv, jako například `overwrite_buffer`. `overwrite_buffer` Třída obsahuje jednu zprávu najednou, ale jeho rozšíří tuto zprávu pro každý z jeho cíle.  
  
 Následující ilustrace znázorňuje sítě pro zpracování bitové kopie:  
  
 ![Sítě pro zpracování image](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")  
  
 `countdown_event` Objekt v tomto příkladu umožňuje sítě pro zpracování bitovou kopii k informování hlavní aplikace, pokud byly zpracovány všechny bitové kopie. `countdown_event` Třídy používá [concurrency::event](../../parallel/concrt/reference/event-class.md) objekt, který má být signalizován hodnota čítače hodnota nula. Hlavní aplikace zvýší čítače pokaždé, když to odešle název souboru k síti. V terminálu uzlu sítě snižuje čítač po zpracování každé bitové kopie. Po hlavní aplikace prochází zadaný adresář, čeká `countdown_event` objekt signál, že jeho čítač dosáhl nula.  
  
 Následující příklad ukazuje `countdown_event` třídy:  
  
 [!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]  
  
 [[Horní](#top)]  
  
##  <a name="complete"></a>Úplný příklad  
 Následující kód ukazuje kompletní příklad. `wmain` Spravuje funkce [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] knihovny a volání `ProcessImages` funkci, aby se proces [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] soubory `Sample Pictures` directory.  
  
 [!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]  
  
 Následující obrázek znázorňuje příklad výstupu. Každé zdrojové bitové kopie je větší než jeho odpovídající upravené bitové kopie.  
  
 ![Ukázkový výstup pro tento příklad](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")  
  
 `Lighthouse`je vytvořená tní Alphin a je proto převedena na ve stupních šedi. `Chrysanthemum`, `Desert`, `Koala`, a `Tulips` mít red jako barvu dominantní a proto mít komponenty modré a zelenou barvu odebrat a jsou ztmaví. `Hydrangeas`, `Jellyfish`, a `Penguins` kritériím výchozí a proto je sépie toned.  
  
 [[Horní](#top)]  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `image-processing-network.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /DUNICODE /EHsc/Link bitové kopie. zpracování network.cpp gdiplus.lib**  
  
## <a name="see-also"></a>Viz také  
 [Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
