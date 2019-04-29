---
title: Upozornění linkerů LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: b527d15310dba70c1bae21e601db17db2900e219
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410236"
---
# <a name="linker-tools-warning-lnk4049"></a>Upozornění linkerů LNK4049

> symbol '*symbol*"definované v"*filename.obj*"importu

[__declspec(dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro *symbol* i v případě, že je definován symbol do souboru objektu *filename.obj* v stejnou bitovou kopii. Odeberte `__declspec(dllimport)` modifikátor, chcete-li vyřešit tato upozornění.

## <a name="remarks"></a>Poznámky

Toto upozornění je vygenerován linkerem při definici symbolu v souboru jednoho objektu a na něj odkazovat pomocí `__declspec(dllimport)` modifikátoru deklarace v jiném.

Upozornění LNK4049 je obecnější verze [LNK4217 upozornění nástrojů Linkeru](linker-tools-warning-lnk4217.md). Linker vydá upozornění LNK4049, pokud nelze určit, jaké funkce nebo objektu soubor odkazován importované symbol.

Běžné případy, ve kterém se vygeneruje LNK4049 místo LNK4217 jsou:

- Při použití [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) možnost.

- Při použití [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) možnost.

Řešení LNK4049, zkuste použijte jeden z následujících postupů:

- Odeberte `__declspec(dllimport)` modifikátor Dopředná deklarace symbolu, který aktivoval LNK4049. Můžete hledat symboly v rámci binárního obrazu pomocí **DUMPBIN** nástroj. **DUMPBIN /SYMBOLS** přepínač zobrazí tabulka symbolů COFF bitové kopie. Další informace o **DUMPBIN** nástroj, najdete v článku [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).

- Dočasně zakážete přírůstkové propojení a optimalizace celého programu. Při nové kompilaci aplikace generuje LNK4217 upozornění, která zahrnuje název funkce, která odkazuje na importované symbol. Odeberte `__declspec(dllimport)` modifikátoru deklarace z importované symbolů a znovu povolit přírůstkové propojení nebo optimalizace celého programu podle potřeby.

I když konečné generovaný kód pracuje správně, je méně efektivní než přímého volání funkce kód generovaný pro volání importované funkce. Toto upozornění nezobrazí při kompilaci pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnost.

Další informace o import a export dat deklarace, naleznete v tématu [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Příklad

Propojení dvou modulů vygeneruje LNK4049. První modul vygeneruje soubor objektu, který obsahuje jeden exportované funkce.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Druhý modul vygeneruje soubor objektu obsahující Dopředná deklarace funkce exportovat v modulu první spolu s volání této funkce uvnitř `main` funkce. Tento modul s modulem první propojení vygeneruje LNK4049. Odeberte `__declspec(dllimport)` modifikátor od deklarace k vyřešení upozornění.

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

## <a name="see-also"></a>Viz také:

[Upozornění Linkerů LNK4217](linker-tools-warning-lnk4217.md) \
[LNK4286 upozornění Linkerů](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)