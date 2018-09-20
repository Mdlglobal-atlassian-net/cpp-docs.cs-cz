---
title: 'Návod: Vytvoření sítě pro zpracování obrazu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c2e1ffc35315d898010e73113d6148fb27e1bad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408043"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Návod: Vytvoření sítě pro zpracování obrázků

Tento dokument ukazuje, jak vytvořit síť asynchronní bloky zpráv, které provádějí zpracování obrázků.

Sítě určuje, které operace mají provést na image na základě jeho vlastnosti. V tomto příkladu *toku dat* vzor trasy Image přes síť. V toku dat modelu nezávislé komponenty aplikace mezi sebou komunikovat odesíláním zpráv. Když komponenta obdrží zprávu, může provést některé akce a výsledku akce předat jiné součásti. Porovnat s *řízení toku* model, ve které aplikace používá řídicí struktury, například, podmíněné příkazy, smyčky a tak dále, k řízení pořadí operací v programu.

Vytvoří síť, která je založená na toku dat *kanálu* úloh. Každá fáze kanálu provádí souběžně části jedné úlohy. Obdobně to je montážní linky u automobilů výroby. Každý vozidla prochází montážní linky, jedné stanice sestaví rámce, jiné nainstaluje modul a tak dále. Povolením více vozidel pro sestavení současně montážní linky poskytuje lepší propustnost než sestavení kompletní vozidel jeden po druhém.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si následující dokumenty:

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Postupy: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

Doporučujeme také, že chápete základy rozhraní GDI + před zahájením tohoto návodu.

##  <a name="top"></a> Oddíly

Tento návod obsahuje následující části:

- [Definice funkce pro zpracování obrázků](#functionality)

- [Vytvoření sítě pro zpracování obrázků](#network)

- [Kompletní příklad](#complete)

##  <a name="functionality"></a> Definice funkce pro zpracování obrázků

Tato část popisuje podporu funkce, které používá sítě pro zpracování obrazu pro práci s imagí, které jsou přečtený z disku.

Následující funkce `GetRGB` a `MakeColor`, extrahování a kombinovat jednotlivých součástí dané barvy v uvedeném pořadí.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

Následující funkce `ProcessImage`, volání daný [std::function](../../standard-library/function-class.md) objektu k transformaci hodnota barvy jednotlivých obrazových bodů v GDI + [rastrový obrázek](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) objektu. `ProcessImage` Funkce používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus pro každý řádek rastrový obrázek paralelní zpracování.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

Následující funkce `Grayscale`, `Sepiatone`, `ColorMask`, a `Darken`, volání `ProcessImage` funkci pro transformaci hodnota barvy jednotlivých obrazových bodů v `Bitmap` objektu. Každá z těchto funkcí používá výraz lambda definovat barvu transformace jeden pixel.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

Následující funkce `GetColorDominance`, také voláním `ProcessImage` funkce. Ale namísto změna hodnoty jednotlivých barev, tato funkce využívá [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) objekty k výpočtu, zda dominuje komponenty červené, zelené nebo modrou barvu na obrázku.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

Následující funkce `GetEncoderClsid`, načte identifikátor třídy pro daný typ MIME pro kodér. Aplikace používá tuto funkci k načtení kodéru pro rastrový obrázek.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Horní](#top)]

##  <a name="network"></a> Vytvoření sítě pro zpracování obrázků

Tato část popisuje, jak vytvořit síť asynchronní bloky zpráv, které provádějí zpracování obrázků na každý obrázek JPEG (JPG) v daném adresáři. Síť provádí následující operace zpracování obrazu:

1. Libovolným obrázkem, který je vytvořen v Tom převeďte na stupně šedé.

1. Pro všechny image, která má jako převládající barvy odeberte zelené a modré složky a potom ztmavení.

1. Další image použijte sépiový tónování.

Síť se vztahuje pouze první zpracování obrázků operace, která odpovídá jednomu z těchto podmínek. Například pokud bitovou kopii je autorem vlastní a má red jako po převládající barvu, image je pouze převést na stupně šedé.

Po síti provádí každé operace zpracování obrázků, uloží image na disk jako soubor rastrového obrázku (BMP).

Následující kroky ukazují, jak vytvořit funkci, která implementuje této sítě pro zpracování obrázků a tato síť se vztahuje na každý obrázek JPEG v daném adresáři.

#### <a name="to-create-the-image-processing-network"></a>K vytvoření sítě pro zpracování obrázků

1. Vytvoření funkce, `ProcessImages`, který přebírá název adresáře na disku.

     [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. V `ProcessImages` funkce, vytváření `countdown_event` proměnné. `countdown_event` Třídy je uveden dále v tomto názorném postupu.

     [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Vytvoření [std::map](../../standard-library/map-class.md) objekt, který přidruží `Bitmap` objekt s jeho původní název souboru.

     [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Přidejte následující kód, který definuje členy zpracování obrazu sítě.

     [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Přidejte následující kód k připojení k síti.

     [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Přidejte následující kód k odesílání do hlavní sítě úplná cesta každého souboru JPEG v adresáři.

     [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Počkejte `countdown_event` proměnné k dosažení nuly.

     [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

Následující tabulka popisuje členy v síti.

|Člen|Popis|
|------------|-----------------|
|`load_bitmap`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) objekt, který načte `Bitmap` objektu z disku a přidá záznam, tím `map` objektu, který chcete přidružit k jeho původní název souboru obrázku.|
|`loaded_bitmaps`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který odesílá načtených imagí filtry zpracování obrázků.|
|`grayscale`|A `transformer` objekt, který převede imagí, které jsou vytvořeny v Tom na stupně šedé. Metadata obrázku používá k určení jeho autor.|
|`colormask`|A `transformer` objekt, který odebere zeleným a modrým barevným z imagí, které mají jako převládající barvy.|
|`darken`|A `transformer` objekt, který ztmaví bitové kopie, které mají jako převládající barvy.|
|`sepiatone`|A `transformer` objekt, který se týká sépiový tónování bitové kopie, které nejsou autorem vlastní a nejsou převážně červené.|
|`save_bitmap`|A `transformer` objekt, který uloží zpracované `image` na disk jako rastrový obrázek. `save_bitmap` Obnoví původní název souboru z `map` objektu a jeho příponu názvu souboru se změní na BMP.|
|`delete_bitmap`|A `transformer` objekt, který uvolní paměť pro Image.|
|`decrement`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) objekt, který funguje jako uzel terminálu v síti. To sníží `countdown_event` objektu na signál pro hlavní aplikaci, že image byla zpracována.|

`loaded_bitmaps` Vyrovnávací paměť zpráv je důležité, protože jako `unbounded_buffer` objektu, nabízí `Bitmap` objekty více příjemcům. Když cílový blok přijme `Bitmap` objektu, `unbounded_buffer` objektu, která nenabízí `Bitmap` objekt do jiné cíle. Proto objektů pořadí, ve kterém můžete propojit `unbounded_buffer` objekt je důležitý. `grayscale`, `colormask`, A `sepiatone` zpráva jednotlivých bloků pomocí filtru tak, aby přijímal pouze určité `Bitmap` objekty. `decrement` Vyrovnávací paměť zpráv je důležité, cíl `loaded_bitmaps` zprávy vyrovnávací paměti, protože všechny přijímá `Bitmap` objekty, které se odmítnul jiné vyrovnávací paměti zpráv. `unbounded_buffer` Šíření zprávy v pořadí je vyžadován objekt. Proto `unbounded_buffer` objekt blokuje, dokud nový cílový blok je propojen a přijímá zprávy, pokud žádná aktuální cílový blok přijímá zprávy.

Pokud vaše aplikace vyžaduje víc zprávy blokuje procesu zprávy, ne jen jedna zpráva blok, který nejprve přijímá zprávy, můžete použít jiný typ bloku zprávy, jako například `overwrite_buffer`. `overwrite_buffer` Třída obsahuje jednu zprávu v čase, ale šíří zprávy pro každý svůj cíl.

Následující ilustrace znázorňuje sítě pro zpracování obrazu:

![Sítě pro zpracování obrazu](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")

`countdown_event` Objekt v tomto příkladu povolí obrazu sítě pro zpracování informovat hlavní aplikace, když byly zpracovány všechny bitové kopie. `countdown_event` Třídy používá [concurrency::event](../../parallel/concrt/reference/event-class.md) objekt, který signalizuje, že když hodnota čítače dosáhne nuly. Hlavní aplikace zvýší čítač pokaždé, když se odešle název souboru k síti. Terminálu uzlu sítě dekrementuje čítače po zpracování každého obrázku. Po hlavní aplikace prochází přes zadaného adresáře, počká na `countdown_event` objektu na signál, že jeho čítač bylo dosaženo nula.

Následující příklad ukazuje `countdown_event` třídy:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Horní](#top)]

##  <a name="complete"></a> Kompletní příklad

Následující kód ukazuje kompletní příklad. `wmain` Spravuje – funkce rozhraní GDI + knihovny a volání `ProcessImages` funkci ke zpracování JPEG soubory `Sample Pictures` adresáře.

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

Ukázkový výstup ukazuje následující obrázek. Každá zdrojová image je vyšší než jeho odpovídající upravenou image.

![Ukázkový výstup například](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")

`Lighthouse` je autorem vlastní Alphin a je proto převedena na ve stupních šedi. `Chrysanthemum`, `Desert`, `Koala`, a `Tulips` mít červenou jako převládající barvy a proto máte odebrat modrá a zelená barevným a jsou ztmaví. `Hydrangeas`, `Jellyfish`, a `Penguins` odpovídat výchozím kritériím a proto je sépiový tón toned.

[[Horní](#top)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `image-processing-network.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /DUNICODE/EHsc/Link bitové kopie. zpracování network.cpp gdiplus.lib**

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
