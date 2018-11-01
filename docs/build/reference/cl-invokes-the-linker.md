---
title: CL vyvolává linker
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: e071209bd09fea17082379bf3f2486866b52c548
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447200"
---
# <a name="cl-invokes-the-linker"></a>CL vyvolává linker

CL vyvolává linker automaticky po kompilaci, pokud se nepoužije možnost /c. CL předá linkeru názvy .obj soubory vytvořené během kompilaci a názvy všechny další soubory zadané na příkazovém řádku. Propojovací program používá možnosti uvedené v proměnné prostředí LINK. Možnost/Link můžete použít k určení možnosti linkeru v příkazovém řádku CL. Možnosti, které následují možností/Link přepíšou nastavení v proměnné prostředí LINK. Možnosti v následující tabulce potlačit propojení.

|Možnost|Popis|
|------------|-----------------|
|/c|Kompilovat bez propojení|
|/ /P E, /EP,|Umožňuje předzpracování bez kompilace nebo propojení|
|/Zg|Generovat prototypy funkcí|
|/ZS|Zkontrolovat syntaxi|

Další informace o propojení naleznete v tématu [možnosti Linkeru](../../build/reference/linker-options.md).

## <a name="example"></a>Příklad

Předpokládejme, že při kompilaci tři C zdrojové soubory: MAIN.c MOD1.c a MOD2.c. Každý soubor obsahuje volání funkce definované v jiném souboru:

- MAIN.c volá funkci `func1` MOD1.c a funkci `func2` v MOD2.c.

- Volání funkce standardní knihovny MOD1.c `printf_s` a `scanf_s`.

- MOD2.c volá grafické funkce s názvem `myline` a `mycircle`, které jsou definovány v knihovně s názvem MYGRAPH.lib.

K vytvoření tohoto programu, proveďte kompilaci s následujícím příkazovým řádkem:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL nejprve zkompiluje zdrojové soubory jazyka C a vytvoří soubory objektů MAIN.obj MOD1.obj a MOD2.obj. Kompilátor umístí do každého souboru .obj název standardní knihovny. Další podrobnosti najdete v tématu [použití knihovny Run-Time](../../build/reference/md-mt-ld-use-run-time-library.md).

CL názvy souborů .obj, spolu s názvem MYGRAPH.lib, předá linkeru. Linker překladu externích odkazů následujícím způsobem:

1. V MAIN.obj, odkaz na `func1` vyřeší v definici MOD1.obj; odkaz na `func2` vyřeší v definici MOD2.obj.

1. V MOD1.obj, odkazy na `printf_s` a `scanf_s` se budou překládat pomocí definice v knihovně, který vyhledá propojovací program s názvem v rámci MOD1.obj.

1. V MOD2.obj, odkazy na `myline` a `mycircle` se budou překládat pomocí definice v MYGRAPH.lib.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)