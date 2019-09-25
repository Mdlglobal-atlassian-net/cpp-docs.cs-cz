---
title: 'Návod: Vytváření sítě pro zpracování obrázků'
ms.date: 04/25/2019
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 680037e0e14c3ebd9171cacf477520e025eecebe
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69512158"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Návod: Vytváření sítě pro zpracování obrázků

Tento dokument ukazuje, jak vytvořit síť asynchronních bloků zpráv, které provádějí zpracování imagí.

Síť určuje, které operace mají být provedeny na obrázku na základě jeho vlastností. V tomto příkladu se používá model *toku* dat pro směrování imagí přes síť. V modelu toku dat vzájemně komunikují nezávislé součásti programu a odesílají zprávy. Když komponenta obdrží zprávu, může provést určitou akci a pak předat výsledek této akce jiné komponentě. Porovnejte je s modelem *toku řízení* , ve kterém aplikace používá řídicí struktury, například podmíněné příkazy, smyčky a tak dále, k řízení pořadí operací v programu.

Síť, která je založena na toku dat, vytvoří *kanál* úloh. Každá fáze kanálu současně provádí část celkové úlohy. Analogie k tomuto je montážní čára pro výrobu automobilu. Vzhledem k tomu, že každá vozidlo projde přes čáru sestavení, jedna stanice sestaví rámec, další nainstaluje modul a tak dále. Když je umožněno sestavovat více vozidel současně, řádka sestavení poskytuje lepší propustnost než sestavování celé vozidlo v jednom okamžiku.

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si následující dokumenty:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

Před zahájením tohoto návodu doporučujeme také pochopit základy rozhraní GDI+.

##  <a name="top"></a>Řezů

Tento návod obsahuje následující oddíly:

- [Definování funkcí zpracování obrázků](#functionality)

- [Vytváření sítě pro zpracování imagí](#network)

- [Úplný příklad](#complete)

##  <a name="functionality"></a>Definování funkcí zpracování obrázků

V této části jsou uvedeny podpůrné funkce, které síť pro zpracování imagí používá pro práci s imagemi, které se čtou z disku.

Následující funkce `GetRGB` a `MakeColor`, extrahují a sloučí jednotlivé komponenty dané barvy, v uvedeném pořadí.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

Následující funkce `ProcessImage`volá daný objekt [std:: Function](../../standard-library/function-class.md) k transformaci hodnoty barvy v jednotlivých pixelech v objektu [bitmapy](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) rozhraní GDI+. Funkce používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) ke zpracování každého řádku bitmapy paralelně. `ProcessImage`

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

`Grayscale`Následující funkce, `Sepiatone`,, `Bitmap` a `Darken`, volají `ProcessImage` funkci pro transformaci hodnoty barvy v jednotlivých pixelech v objektu. `ColorMask` Každá z těchto funkcí používá výraz lambda k definování transformace barev jednoho pixelu.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

Následující funkce `GetColorDominance`,, `ProcessImage` volá také funkci. Místo toho, aby se změnila hodnota každé barvy, tato funkce používá objekty [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovatelné k výpočtu, zda je obrázek v komponentě červená, zelená nebo modrá.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

Následující funkce `GetEncoderClsid`načte identifikátor třídy pro daný typ MIME kodéru. Aplikace tuto funkci používá k načtení kodéru pro rastrový obrázek.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Nahoře](#top)]

##  <a name="network"></a>Vytváření sítě pro zpracování imagí

Tato část popisuje, jak vytvořit síť asynchronních bloků zpráv, které provádějí zpracování imagí v každé imagi JPEG (. jpg) v daném adresáři. Síť provádí následující operace zpracování imagí:

1. Pro všechny obrázky, které jsou vytvořené pomocí, proveďte převod na stupně šedi.

1. Pro všechny obrázky, které mají jako dominantní barvu červenou barvu, odeberte zelené a modré komponenty a pak ji ztmaví.

1. U všech ostatních imagí použijte sépiový tón Toning.

Síť se vztahuje pouze na první operaci zpracování obrázku, která odpovídá jedné z těchto podmínek. Například pokud je obrázek vytvořený tak, aby měl červenou barvu jako dominantní barvu, obrázek se převede jenom na stupně šedi.

Jakmile síť provede jednotlivé operace zpracování imagí, uloží image na disk jako soubor rastrového obrázku (. bmp).

Následující kroky ukazují, jak vytvořit funkci, která implementuje tuto síť pro zpracování imagí a tuto síť použije na každý obrázek JPEG v daném adresáři.

#### <a name="to-create-the-image-processing-network"></a>Vytvoření sítě pro zpracování imagí

1. Vytvořte funkci `ProcessImages`, která převezme název adresáře na disku.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. `ProcessImages` Ve funkci`countdown_event` Vytvořte proměnnou. `countdown_event` Třída je uvedena dále v tomto návodu.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Vytvořte objekt [std:: map](../../standard-library/map-class.md) , který přidruží `Bitmap` objekt k původnímu názvu souboru.

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Přidejte následující kód k definování členů sítě pro zpracování obrázků.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Přidejte následující kód pro připojení sítě.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Přidejte následující kód, který bude odeslán do hlavní části sítě úplná cesta k jednotlivým souborům JPEG v adresáři.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Počkejte, až proměnná dosáhne hodnoty nula. `countdown_event`

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

V následující tabulce jsou popsány členové sítě.

|Člen|Popis|
|------------|-----------------|
|`load_bitmap`|Objekt [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) , který načte `Bitmap` objekt z disku a přidá položku do `map` objektu k přidružení obrázku k původnímu názvu souboru.|
|`loaded_bitmaps`|Objekt [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , který odesílá načtené obrázky do filtrů zpracování imagí.|
|`grayscale`|`transformer` Objekt, který převede obrázky, které jsou vytvořeny tak, že vede na stupně šedi. K určení jeho autora používá metadata obrázku.|
|`colormask`|`transformer` Objekt, který odebere zelenou a modrou barvu barev z obrázků, které mají červenou barvu jako dominantní barvu.|
|`darken`|`transformer` Objekt, který ztmaví obrázky, které mají jako dominantní barvu červenou barvu.|
|`sepiatone`|`transformer` Objekt, který aplikuje Sépiový tón Toning na obrázky, které nejsou vytvořeny tak, aby a nebyly převážně červené.|
|`save_bitmap`|Objekt, který ukládá zpracované `image` na disk jako rastrový obrázek. `transformer` `save_bitmap`Načte původní název souboru z `map` objektu a změní jeho příponu názvu souboru na. bmp.|
|`delete_bitmap`|`transformer` Objekt, který uvolní paměť pro obrázky.|
|`decrement`|Objekt [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) , který funguje jako uzel terminálu v síti. Snižuje `countdown_event` objekt tak, aby byl signálem k hlavní aplikaci, na kterou byl obrázek zpracován.|

Vyrovnávací paměť `unbounded_buffer` `Bitmap`zprávje důležitá, protože jako objekt nabízí objekty pro více přijímačů. `loaded_bitmaps` Když cílový blok akceptuje `Bitmap` objekt `unbounded_buffer` , `Bitmap` objekt tento objekt nenabídne jiným cílům. Proto je důležité pořadí, ve kterém propojíte objekty `unbounded_buffer` s objektem. Bloky `grayscale`zpráv `colormask`, `Bitmap` a `sepiatone` jsou v každém z nich použity filtr pro příjem pouze určitých objektů. Vyrovnávací paměť `loaded_bitmaps` `Bitmap`zprávje důležitým cílem vyrovnávací paměti zpráv, protože přijímá všechny objekty, které jsou odmítnuty jinými vyrovnávacími pamětmi zpráv. `decrement` K šíření zpráv v daném pořadí je vyžadován objekt.`unbounded_buffer` `unbounded_buffer` Proto objekt blokuje, dokud není propojen nový cílový blok a přijímá zprávu, pokud žádný aktuální cílový blok tuto zprávu nepřijme.

Pokud vaše aplikace vyžaduje, aby zpráva zpracovala více bloků zpráv, místo pouze jednoho bloku zpráv, který zprávu nejprve přijme, můžete použít jiný typ bloku zpráv, například `overwrite_buffer`. `overwrite_buffer` Třída uchovává jednu zprávu v čase, ale šíří tuto zprávu do každého z jeho cílů.

Následující ilustrace znázorňuje síť pro zpracování imagí:

![Síť pro zpracování imagí](../../parallel/concrt/media/concrt_imageproc.png "Síť pro zpracování imagí")

`countdown_event` Objekt v tomto příkladu umožňuje, aby síť pro zpracování imagí informovala hlavní aplikaci při zpracování všech imagí. Třída používá objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) k signalizaci, že hodnota čítače dosáhne nuly. `countdown_event` Hlavní aplikace zvýší čítač pokaždé, když pošle název souboru do sítě. Uzel terminálu sítě snižuje čítač po zpracování jednotlivých imagí. Poté, co hlavní aplikace projde zadaný adresář, počká `countdown_event` , až objekt dorazí na signál, že jeho čítač dosáhl nuly.

Následující příklad ukazuje `countdown_event` třídu:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Nahoře](#top)]

##  <a name="complete"></a>Úplný příklad

Následující kód ukazuje kompletní příklad. Funkce spravuje knihovnu GDI+ a `ProcessImages` volá funkci pro zpracování souborů JPEG v `Sample Pictures` adresáři. `wmain`

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

Na následujícím obrázku vidíte ukázkový výstup. Každý zdrojový obraz je nad svým odpovídajícím upraveným obrázkem.

![Ukázkový výstup pro příklad](../../parallel/concrt/media/concrt_imageout.png "Ukázkový výstup pro příklad")

`Lighthouse`je vytvořená Alphin, a proto se převede na stupně šedi. `Chrysanthemum`, `Desert`, `Koala` a`Tulips` mají jako dominantní barvu červenou barvu, a proto se odeberou modré a zelené barevné komponenty a jsou tmavší. `Hydrangeas`, `Jellyfish` a`Penguins` odpovídají výchozím kritériím, a proto jsou Sépiový tón Toned.

[[Nahoře](#top)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `image-processing-network.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/DUNICODE/EHsc Image-Processing-Network. cpp/Link Gdiplus. lib**

## <a name="see-also"></a>Viz také:

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
