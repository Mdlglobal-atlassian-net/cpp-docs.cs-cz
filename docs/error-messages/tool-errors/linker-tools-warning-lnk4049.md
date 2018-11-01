---
title: Upozornění linkerů LNK4049
ms.date: 11/04/2016
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: ed17a6014ddf420256848c87a90a37f190a0663e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429074"
---
# <a name="linker-tools-warning-lnk4049"></a>Upozornění linkerů LNK4049

lokálně definovaný symbol importovat symbol

Symbol byla exportovaná z i importovat do programu.

Toto upozornění je vygenerován linkerem při deklaraci symbolu pomocí `__declspec(dllexport)` atributu v souboru jednoho objektu třídy úložiště a na něj odkazovat pomocí `__declspec(dllimport)` atribut v jiném.

Upozornění LNK4049 je obecnější verze [LNK4217 upozornění nástrojů Linkeru](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). Linker generuje LNK4049 upozornění, když nemůže určit z funkce, které bylo odkazováno importované symbol.

Běžné případy, ve kterém se vygeneruje LNK4049 místo LNK4217 jsou:

- Přírůstkové propojování pomocí provádí [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) možnost.

- Pomocí provádí optimalizace celého programu [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) možnost.

Řešení LNK4049, zkuste použijte jeden z následujících akcí:

- Odeberte `__declspec(dllimport)` název deklarace z Dopředná deklarace symbolu, která aktivovala LNK4049. Můžete hledat symboly v rámci binárního obrazu pomocí **DUMPBIN** nástroj. **DUMPBIN/symboly** přepínač zobrazí tabulka symbolů COFF bitové kopie. Další informace o **DUMPBIN** nástroj, najdete v článku [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).

- Dočasně zakážete přírůstkové propojení a optimalizace celého programu. Opětovnou kompilací aplikace vygeneruje LNK4217 upozornění, která bude obsahovat název funkce, ze které bylo odkazováno importované symbol. Odeberte `__declspec(dllimport)` deklarace z importované symbolů a Povolit přírůstkové propojení nebo optimalizace celého programu podle potřeby.

I když konečné generovaný kód se bude chovat správně, je méně efektivní než přímého volání funkce kód generovaný pro volání importované funkce. Toto upozornění se nezobrazí při kompilaci pomocí volby [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Další informace o import a export dat deklarace, naleznete v tématu [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Příklad

Propojení dvou modulů vygeneruje LNK4049. První modul vygeneruje soubor objektu, který obsahuje jeden exportované funkce.

```
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

## <a name="example"></a>Příklad

Druhý modul vygeneruje soubor objektu obsahující Dopředná deklarace funkce exportovat v modulu první spolu s volání této funkce uvnitř `main` funkce. Tento modul s modulem první propojení vygeneruje LNK4049. Odebírá `__declspec(dllimport)` deklarace vyřeší upozornění.

```
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>Viz také

[Upozornění linkerů LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)