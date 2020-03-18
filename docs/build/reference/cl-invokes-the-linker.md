---
title: CL vyvolává linker
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: 1f9bb466ae89b8e3491b027a98b28935e7c8b523
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440181"
---
# <a name="cl-invokes-the-linker"></a>CL vyvolává linker

CL automaticky vyvolá linker po zkompilování, pokud se nepoužije možnost/c. CL předá linkeru názvy souborů. obj vytvořených během kompilování a názvy dalších souborů, které jsou zadány v příkazovém řádku. Linker používá možnosti uvedené v proměnné prostředí propojení. Můžete použít možnost/Link k zadání možností linkeru na příkazovém řádku CL. Možnosti, které následují po možnosti/Link, přepisují ty v proměnné prostředí propojení. Možnosti v následující tabulce potlačí propojování.

|Možnost|Popis|
|------------|-----------------|
|/c|Kompilovat bez propojení|
|/E, /EP, /P|Předzpracování bez kompilování nebo propojení|
|/ZG|Generování prototypů funkcí|
|/Zs|Ověřit syntaxi|

Další podrobnosti o propojování najdete v tématu [Možnosti linkeru MSVC](linker-options.md).

## <a name="example"></a>Příklad

Předpokládejme, že kompilujete tři zdrojové soubory jazyka C: MAIN. c, MOD1. c a MOD2. c. Každý soubor obsahuje volání funkce definované v jiném souboru:

- MAIN. c volá funkci `func1` v MOD1. c a funkce `func2` v MOD2. c.

- MOD1. c volá standardní funkce knihovny `printf_s` a `scanf_s`.

- MOD2. c volá grafické funkce s názvem `myline` a `mycircle`, které jsou definovány v knihovně s názvem MYGRAPH. lib.

Chcete-li sestavit tento program, zkompilujte pomocí následujícího příkazového řádku:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL nejprve zkompiluje zdrojové soubory jazyka C a vytvoří objekty Object Files MAIN. obj, MOD1. obj a MOD2. obj. Kompilátor umístí název standardní knihovny do každého souboru. obj. Další podrobnosti najdete v tématu [použití knihovny run-time](md-mt-ld-use-run-time-library.md).

CL předá do linkeru názvy souborů. obj společně s názvem MYGRAPH. lib. Linker vyřeší externí odkazy následujícím způsobem:

1. V MAIN. obj je odkaz na `func1` přeložen pomocí definice v MOD1. obj; odkaz na `func2` je vyřešen pomocí definice v MOD2. obj.

1. V MOD1. obj jsou odkazy na `printf_s` a `scanf_s` přeloženy pomocí definic v knihovně, kterou linker nalezne v rámci MOD1. obj.

1. V MOD2. obj jsou odkazy na `myline` a `mycircle` přeloženy pomocí definic v MYGRAPH. lib.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Nastavení možností kompilátoru](compiler-command-line-syntax.md)
