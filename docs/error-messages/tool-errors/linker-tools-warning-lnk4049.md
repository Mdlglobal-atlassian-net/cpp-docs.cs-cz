---
title: Upozornění linkerů LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: a8e4416eafd47f584de4ab1c83aa7303cab0440a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194132"
---
# <a name="linker-tools-warning-lnk4049"></a>Upozornění linkerů LNK4049

> symbol*symbol*definovaný v*souboru filename. obj*je importovaný.

byl zadán [__declspec (dllimport)](../../cpp/dllexport-dllimport.md) pro *symbol* , i když je symbol definován ve stejném obrázku jako soubor s *názvem souboru. obj* . Odeberte modifikátor `__declspec(dllimport)` pro vyřešení tohoto upozornění.

## <a name="remarks"></a>Poznámky

Toto upozornění je generován linkerem při definování symbolu v jednom souboru objektu a jeho odkazování pomocí modifikátoru `__declspec(dllimport)` deklarace v jiném.

Warning LINKERŮ LNK4049 je obecnější verze [linkerů LNK4217 nástrojů linkeru upozornění](linker-tools-warning-lnk4217.md). Linker generuje upozornění LINKERŮ LNK4049, když nemůže určit, na kterou funkci nebo soubor objektu odkazoval importovaný symbol.

Běžné případy, kdy se vygeneruje LINKERŮ LNK4049 místo LINKERŮ LNK4217:

- Při použití možnosti [/incremental](../../build/reference/incremental-link-incrementally.md)

- Při použití možnosti [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)

Chcete-li vyřešit LINKERŮ LNK4049, zkuste použít jeden z následujících postupů:

- Odeberte modifikátor `__declspec(dllimport)` z dopředné deklarace symbolu, který spustil LINKERŮ LNK4049. Symboly v binární imagi můžete hledat pomocí nástroje **DUMPBIN** . Přepínač **DUMPBIN/Symbols** zobrazí tabulku symbolů COFF obrázku. Další informace o nástroji **DUMPBIN** naleznete v tématu [Reference pro DUMPBIN](../../build/reference/dumpbin-reference.md).

- Dočasně zakažte přírůstkové propojování a optimalizaci celého programu. Při překompilování aplikace generuje upozornění LINKERŮ LNK4217, které obsahuje název funkce odkazující na importovaný symbol. Odeberte z importovaného symbolu `__declspec(dllimport)` modifikátor deklarace a v případě potřeby znovu povolte přírůstkové propojování nebo optimalizaci celého programu.

I když se výsledný generovaný kód chová správně, kód vygenerovaný pro volání importované funkce je méně efektivní než volání funkce přímo. Toto upozornění se nezobrazí při kompilaci pomocí možnosti [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Další informace o importu a exportu dat deklarace naleznete v tématu [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Příklad

Propojením následujících dvou modulů se vygeneruje LINKERŮ LNK4049. První modul generuje soubor objektu obsahující jednu exportovanou funkci.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Druhý modul generuje soubor objektu obsahující dopřednou deklaraci do funkce exportované v prvním modulu, spolu s voláním této funkce uvnitř funkce `main`. Propojením tohoto modulu s prvním modulem se vygeneruje LINKERŮ LNK4049. Odeberte modifikátor `__declspec(dllimport)` z deklarace pro vyřešení upozornění.

```cpp
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

[Linkerů lnk4217 \ upozornění na nástroje linkeru](linker-tools-warning-lnk4217.md)
[LNK4286 \ upozornění na nástroje linkeru](linker-tools-warning-lnk4286.md)
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
