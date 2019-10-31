---
title: Bloky popisů
description: Nástroj NMAKE používá bloky popisů k přidružení cílů, závislostí a příkazů v souboru pravidel.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144533"
---
# <a name="description-blocks"></a>Bloky popisů

Popis bloků tvoří základní část souboru pravidel. Popisují *cíle*, soubory, které se mají vytvořit, a jejich *závislosti*, soubory potřebné k vytvoření cílů. Blok popisu může obsahovat *příkazy*, které popisují, jak vytvořit cíle ze závislostí. Blok popisu je řádek závislosti, volitelně následovaný blokem příkazů:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Řádky závislosti

*Řádek závislosti* Určuje jeden nebo více cílů a nula nebo více závislých prvků. Pokud cíl neexistuje nebo má dřívější časové razítko než závislý, spustí aplikace NMAKE příkazy v bloku příkazů. NMAKE také spustí blok příkazů, pokud je cílem [pseudotarget](pseudotargets.md). Tady je příklad řádku závislosti:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

V této řádce závislosti je `hi_bye.exe` cílem. Jeho závislosti jsou `hello.obj`, `goodbye.obj`a `helper.lib`. Řádek závislosti oznamuje nástroji NMAKE, aby vytvořil cíl pokaždé, když `hello.obj`, `goodbye.obj`nebo `helper.lib` se změnila v nedávné době od `hi_bye.exe`.

Cíl musí být na začátku řádku. Nedá se odsazovat mezerami ani kartami. Použijte dvojtečku (`:`) k oddělení cílů od závislých prvků. Mezi cíli je povolená mezera nebo tabulátory, oddělovač dvojtečky (`:`) a závislé prvky. Chcete-li rozdělit čáru závislosti, použijte zpětné lomítko (`\`) po cíli nebo závislosti.

Před spuštěním příkazového bloku NMAKE zkontroluje všechny závislosti a veškerá příslušná pravidla odvození a vytvoří *strom závislostí*. Strom závislosti určuje kroky požadované k plnému aktualizaci cíle. NMAKE kontroluje rekurzivní kontrolu, jestli je závislá na cíli v jiném seznamu závislostí. Po sestavení stromu závislostí NMAKE kontroluje časová razítka. Pokud jsou jakékoli závislé položky ve stromové struktuře novější než cíl, aplikace NMAKE vytvoří cíl.

## <a name="targets"></a>Cíle

Oddíl targets na řádku závislosti Určuje jeden nebo více cílů. Cílem může být libovolný platný název souboru, název adresáře nebo [pseudotarget](pseudotargets.md). Pomocí jedné nebo více mezer nebo karet oddělte více cílů. Cíle nerozlišují velká a malá písmena. Cesty jsou povoleny s názvy souborů. Cíl a jeho cesta nesmí být delší než 256 znaků. Pokud je cíl předcházející dvojtečkě jedním znakem, použijte oddělení mezer. V opačném případě NMAKE interpretuje kombinaci písmen-dvojtečky jako specifikátor jednotky.

### <a name="multiple-targets"></a>Více cílů

NMAKE vyhodnocuje více cílů v jedné závislosti, jako kdyby byly zadány v bloku samostatného popisu.

Například toto pravidlo:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

je vyhodnocen jako:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>Kumulativní závislosti

Závislosti jsou v bloku popisu kumulativní, pokud se cíl opakuje.

Například tato sada pravidel

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

je vyhodnocen jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Pokud máte více cílů v několika řádcích závislosti v rámci jednoho bloku s popisem, NMAKE je vyhodnocuje, jako kdyby byly zadány v bloku samostatného popisu. Pouze cíle v poslední čáře závislosti však používají blok příkazů. NMAKE se pokusí použít pro ostatní cíle pravidlo odvození.

Například tato sada pravidel

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

je vyhodnocen jako:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>Cíle ve více blocích popisů

Chcete-li aktualizovat cíl ve více než jednom bloku popisu pomocí různých příkazů, zadejte dvě po sobě jdoucí dvojtečky (::) mezi cíli a závislými prvky.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>Vedlejší účinky závislosti

Cíl můžete zadat pomocí dvojtečky (:) ve dvou řádcích závislosti v různých umístěních. Pokud se příkazy zobrazí po pouze jednom z řádků, NMAKE interpretuje závislosti, jako kdyby byly řádky sousedící nebo kombinované. Nevyvolává odvozené pravidlo pro závislost, která nemá žádné příkazy. Místo toho modul NMAKE předpokládá, že závislosti patří do jednoho bloku popisu, a spustí příkazy určené druhou závislostí. Vezměte v úvahu tuto sadu pravidel:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

je vyhodnocen jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

K tomuto efektu nedochází, pokud se používá dvojtečka (`::`). Například tato sada pravidel:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

je vyhodnocen jako:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>Pseudocíle

*Pseudotarget* je popisek použitý místo názvu souboru na lince závislosti. Je interpretována jako soubor, který neexistuje, a proto je zastaralá. NMAKE předpokládá, že časové razítko pseudotarget je stejné jako poslední ze všech jeho závislých prvků. Pokud se nejedná o žádné závislé položky, předpokládá se aktuální čas. Pokud se jako cíl použije pseudotarget, jeho příkazy se vždycky spustí. Pseudotarget použité jako závislé se musí také zobrazit jako cíl v jiné závislosti. Nicméně tato závislost nemusí mít blok příkazů.

Názvy pseudotarget se řídí pravidly syntaxe filename pro cíle. Pokud ale název nemá příponu, může překročit limit osmi znaků pro názvy souborů a může být dlouhý až 256 znaků.

Pseudocíle jsou užitečné, pokud chcete, aby NMAKE vytvořilo automaticky více než jeden cíl. NMAKE sestaví jenom cíle zadané v příkazovém řádku. Nebo, pokud není zadán žádný cíl příkazového řádku, sestavení sestaví pouze první cíl v první závislosti v souboru pravidel. Můžete aplikaci NMAKE sdělit, aby vytvořila více cílů bez nutnosti jejich uvedení na příkazovém řádku jednotlivě. Napište blok popisu se závislostí obsahující pseudotarget a uveďte cíle, které chcete sestavit jako své závislé prvky. Pak umístěte tento blok popisu nejprve do souboru pravidel nebo zadejte pseudotarget do příkazového řádku NMAKE.

V tomto příkladu je aktualizace pseudotarget.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Při vyhodnocení aktualizace NMAKE zkopíruje všechny soubory v aktuálním adresáři do zadané jednotky a adresáře.

V následujícím souboru pravidel `all` pseudotarget sestaví `project1.exe` a `project2.exe`, pokud je na příkazovém řádku zadán buď `all` nebo žádný cíl. Pseudotarget `setenv` změní proměnnou prostředí LIB předtím, než se aktualizují soubory `.exe`:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>Závislé položky

V řádku závislostí zadejte nula nebo více závislých prvků za dvojtečkou (`:`) nebo dvojitou dvojtečkou (`::`), přičemž použijte libovolný platný název souboru nebo [pseudotarget](pseudotargets.md). Více závislých prvků rozdělte pomocí jedné nebo více mezer nebo karet. Závislé objekty nerozlišují velká a malá písmena. Cesty jsou povoleny s názvy souborů.

### <a name="inferred-dependents"></a>Odvozené závislé objekty

Spolu se závislými prvky, které explicitně zadáte na řádku závislosti, může NMAKE předpokládat odvozenou *závislost*. Odvozená závislá je odvozená od pravidla odvození a je vyhodnocena před explicitními závislými. Pokud je odvozená závislá data v porovnání s cílem, modul NMAKE vyvolá blok příkazů pro závislost. Pokud odvozená závislá neexistuje nebo je ve srovnání se svými vlastními závislostmi odvozená, modul NMAKE nejprve aktualizuje odvozené závislé položky. Další informace o odvozených závislých prvkůch naleznete v tématu [pravidla odvození](inference-rules.md).

### <a name="search-paths-for-dependents"></a>Cesty hledání závislých prvků

Můžete zadat volitelnou cestu pro hledání každého závislého prvku. Tady je syntaxe pro určení sady adresářů k hledání:

> **{** _Directory_\[ **;** _adresář_...] **}** _závislé_

Názvy adresářů vložte do složených závorek (`{ }`). Více adresářů oddělte středníkem (`;`). Nejsou povoleny mezery ani tabulátory. NMAKE hledá závislé položky jako první v aktuálním adresáři a potom v seznamu adresářů v zadaném pořadí. Pomocí makra můžete určit část nebo celou cestu pro hledání. Tato cesta pro hledání používá pouze zadaný závislý parametr.

#### <a name="directory-search-path-example"></a>Příklad cesty hledání adresáře

Tato čára závislosti ukazuje, jak vytvořit specifikace adresáře pro hledání:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

Cílový `reverse.exe` má jeden závislý `retro.obj`. Seznam uzavřený ve složených závorkách určuje dva adresáře. NMAKE nejprve vyhledává `retro.obj` v aktuálním adresáři. Pokud tam není, NMAKE vyhledá `\src\omega` adresář a pak `e:\repo\backwards` adresář.

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)
