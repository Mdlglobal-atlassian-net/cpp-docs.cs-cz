---
title: Bloky popisů
description: NMAKE používá popis bloky přidružit cíle, závislosti a příkazy v makefile.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322266"
---
# <a name="description-blocks"></a>Bloky popisů

Popis bloky tvoří jádro makefile. Popisují *cíle*nebo soubory k vytvoření a jejich *závislosti*soubory potřebné k vytvoření cílů. Blok popisu může obsahovat *příkazy*, které popisují, jak vytvořit cíle ze závislostí. Blok popisu je řádek závislosti, za nímž volitelně následuje blok příkazů:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Řádky závislostí

*Řádek závislostí* určuje jeden nebo více cílů a nula nebo více závislých. Pokud cíl neexistuje nebo má dřívější časové razítko než závislé, NMAKE provede příkazy v bloku příkazů. NMAKE také provede blok příkazů, pokud je cíl [pseudotarget](pseudotargets.md). Tady je příklad řádku závislostí:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

V tomto řádku `hi_bye.exe` závislosti je cíl. Jeho závislosti `hello.obj`jsou `goodbye.obj`, `helper.lib`, a . Řádek závislostí říká NMAKE sestavit `hello.obj`cíl `goodbye.obj`vždy `helper.lib` , , `hi_bye.exe`nebo se změnil v poslední době než .

Cíl musí být na začátku řádku. Nelze ji odsadit s mezerami nebo kartami. Pomocí dvojtečky (`:`) oddělte cíle od závislých osob. Mezery nebo tabulátory jsou povoleny mezi cíli, oddělovačem dvojtečky (`:`) a závislými položkami. Chcete-li rozdělit řádek závislosti, použijte`\`zpětné lomítko ( ) za cíl nebo závislé.

Před spuštěním příkazových bloků NMAKE prohledá všechny závislosti a všechna příslušná odvozená pravidla k vytvoření *stromu závislostí*. Strom závislostí určuje kroky potřebné k úplné aktualizaci cíle. NMAKE rekurzivně kontroluje, zda je závislý sám cíl v jiném seznamu závislostí. Po sestavení stromu závislostí NMAKE zkontroluje časová razítka. Pokud všechny závislé osoby ve stromu jsou novější než cíl, NMAKE vytvoří cíl.

## <a name="targets"></a><a name="targets"></a>Cíle

Cílová část řádku závislostí určuje jeden nebo více cílů. Cíl může být libovolný platný název souboru, název adresáře nebo [pseudocíl](pseudotargets.md). Oddělte více cílů pomocí jedné nebo více mezer nebo karet. Cíle nerozlišují malá a velká písmena. Cesty jsou povoleny s názvy souborů. Cíl a jeho cesta nesmí překročit 256 znaků. Pokud je cíl předcházející dvojtečku jeden znak, použijte oddělovací mezeru. V opačném případě NMAKE interpretuje kombinaci písmeno-dvojtečka jako specifikátor jednotky.

### <a name="multiple-targets"></a><a name="multiple-targets"></a>Více cílů

NMAKE vyhodnocuje více cílů v jedné závislosti, jako by byly zadány v samostatném bloku popisu.

Například toto pravidlo:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

se vyhodnocuje jako:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>Kumulativní závislosti

Závislosti jsou kumulativní v bloku popisu, pokud se cíl opakuje.

Například tento soubor pravidel,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

se vyhodnocuje jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Pokud máte více cílů ve více řádcích závislostí v jednom bloku popisu, NMAKE je vyhodnotí, jako by byly zadány v samostatném bloku popisu. Pouze cíle v poslední linii závislosti však používají blok příkazů. NMAKE se pokusí použít pravidlo odvození pro ostatní cíle.

Například tento soubor pravidel,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

se vyhodnocuje jako:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>Cíle ve více popisech bloků

Chcete-li aktualizovat cíl ve více než jednom bloku popisu pomocí různých příkazů, zadejte dvě po sobě jdoucí dvojtečky (::) mezi cíli a závislými osobami.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>Vedlejší účinky závislosti

Můžete zadat cíl s dvojtečkou (:) ve dvou řádcích závislostí v různých umístěních. Pokud příkazy se zobrazí pouze po jednom z řádků, NMAKE interpretuje závislosti, jako kdyby řádky byly přilehlé nebo kombinované. Nevyvolá pravidlo odvození pro závislost, která nemá žádné příkazy. Místo toho NMAKE předpokládá, že závislosti patří do jednoho bloku popisu a provede příkazy zadané s druhou závislostí. Zvažte tuto sadu pravidel:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

se vyhodnocuje jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

K tomuto efektu nedochází,`::`pokud se používá dvojitá dvojtečka ( ). Například tato sada pravidel:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

se vyhodnocuje jako:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>Pseudocíle

*Pseudotarget* je popisek používaný místo názvu souboru v řádku závislostí. Je interpretován jako soubor, který neexistuje, a tak je zastaralý. NMAKE předpokládá, že časové razítko pseudocíle je stejné jako poslední ze všech jeho závislých. Pokud nemá žádné závislé položky, předpokládá se aktuální čas. Pokud pseudotarget se používá jako cíl, jeho příkazy jsou vždy provedeny. Pseudocíl používaný jako závislý musí také zobrazit jako cíl v jiné závislosti. Tato závislost však nemusí mít blok příkazů.

Pseudocílové názvy se řídí syntaxí názvů souborů pro cíle. Pokud však název nemá příponu, může překročit limit 8 znaků pro názvy souborů a může mít dlouhou až 256 znaků.

Pseudocíle jsou užitečné, pokud chcete, aby NMAKE automaticky vytvořil více než jeden cíl. NMAKE pouze staví cíle zadané na příkazovém řádku. Nebo pokud není zadán žádný cíl příkazového řádku, vytvoří pouze první cíl v první závislosti v makefile. Můžete říct NMAKE vytvořit více cílů bez jejich zařazení jednotlivě na příkazovém řádku. Napište blok popisu se závislostí obsahující pseudocíl a uveďte cíle, které chcete vytvořit jako jeho závislé položky. Potom umístěte tento blok popisu nejprve do makefile nebo zadejte pseudotarget na příkazovém řádku NMAKE.

V tomto příkladu UPDATE je pseudotarget.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Při vyhodnocení update NMAKE zkopíruje všechny soubory v aktuálním adresáři na zadanou jednotku a adresář.

V následujícím makefile pseudotarget `all` vytvoří `project1.exe` oba `project2.exe` a `all` pokud jeden nebo žádný cíl je zadán na příkazovém řádku. Pseudocíl `setenv` změní proměnnou prostředí `.exe` LIB před aktualizací souborů:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>Rodinných příslušníků

V řádku závislosti zadejte nulu nebo více`:`závislých jednotek`::`za dvojtečkou ( ) nebo dvojitou dvojtečkou ( ) pomocí libovolného platného názvu souboru nebo [pseudocíle](pseudotargets.md). Oddělte více závislých osob pomocí jedné nebo více mezer nebo karet. Závislé položky nerozlišují malá a velká písmena. Cesty jsou povoleny s názvy souborů.

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>Odvozené závislé položky

Spolu s závislými osobami, které explicitně uvádíte v řádku závislostí, nmake může předpokládat *odvozené závislé*. Odvozené závislé je odvozen z pravidla odvození a je vyhodnocena před explicitní závislé položky. Pokud je odvozená závislá osoba ve srovnání s jeho cílem zastaralá, NMAKE vyvolá blok příkazů pro závislost. Pokud odvozené závislé neexistuje nebo je zastaralý ve srovnání s jeho vlastní závislé, NMAKE nejprve aktualizuje odvozené závislé. Další informace o odvozených závislých položkách naleznete [v tématu Inference rules](inference-rules.md).

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>Hledat cesty pro závislé osoby

Pro každou závislou položku můžete určit volitelnou cestu hledání. Zde je syntaxe pro určení sady adresářů pro vyhledávání:

> **{**_adresář_\[**;** _adresář_...] **}**_závislý_

Názvy adresářů uzavřete do závorek (`{ }`). Oddělte více adresářů`;`středníkem ( ). Nejsou povoleny žádné mezery ani karty. NMAKE vyhledá závislé nejprve v aktuálním adresáři a potom v seznamu adresářů v zadaném pořadí. Makro můžete použít k určení části nebo celé cesty hledání. Tuto cestu hledání používá pouze zadaná závislá osoba.

#### <a name="directory-search-path-example"></a>Příklad cesty hledání adresáře

Tento řádek závislostí ukazuje, jak vytvořit specifikaci adresáře pro hledání:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

Cíl `reverse.exe` má jednu `retro.obj`závislou. Seznam složených závorek určuje dva adresáře. NMAKE vyhledá `retro.obj` v aktuálním adresáři jako první. Pokud tam není, NMAKE prohledá `\src\omega` adresář, `e:\repo\backwards` pak adresář.

## <a name="see-also"></a>Viz také

[Odkaz NMAKE](nmake-reference.md)
