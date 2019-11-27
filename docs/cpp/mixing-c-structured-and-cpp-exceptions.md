---
title: Kombinování (strukturovaných) C++ a výjimek
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246464"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Kombinování (strukturovaných) C++ a výjimek

Pokud chcete zapisovat přenosný kód, použití strukturovaného zpracování výjimek (SEH) v C++ programu není doporučeno. Někdy ale můžete chtít kompilovat pomocí [/EHa](../build/reference/eh-exception-handling-model.md) a kombinovat strukturované výjimky a C++ zdrojový kód a potřebovat nějaké zařízení pro zpracování obou druhů výjimek. Vzhledem k tomu, že obslužná rutina strukturované výjimky nemá žádný koncept objektů nebo zadaných výjimek, nemůže zpracovat C++ výjimky vyvolané kódem. C++ Nicméně obslužné rutiny **catch** mohou zpracovávat strukturované výjimky. C++syntaxe zpracování výjimek (**Try**, **throw**, **catch**) není kompilátorem jazyka C přijata, ale syntaxe zpracování strukturované výjimky ( **__try**, **__except**, **__finally**) je podporována C++ kompilátorem.

Informace [](../c-runtime-library/reference/set-se-translator.md) o tom, jak zpracovávat strukturované výjimky jako C++ výjimky, najdete v tématu _set_se_translator.

Pokud kombinujete strukturované a C++ výjimky, pamatujte na tyto potenciální problémy:

- Výjimky jazyka C++ a strukturované výjimky nelze kombinovat v rámci stejné funkce.

- Obslužné rutiny ukončení ( **__finally** bloky) jsou vždy spouštěny, i během unwindy po vyvolání výjimky.

- C++zpracování výjimek může zachytit a zachovat sémantiku unwind ve všech modulech kompilovaných pomocí možností kompilátoru [/eh](../build/reference/eh-exception-handling-model.md) , které umožňují sémantiku unwind.

- Mohou existovat situace, ve kterých nejsou funkce destruktoru volány pro všechny objekty. Například pokud dojde k strukturované výjimce při pokusu o provedení volání funkce prostřednictvím neinicializovaného ukazatele funkce a tato funkce přebírá objekty parametrů, které byly vytvořeny před voláním, nejsou volány destruktory těchto objektů. během unwind zásobníku.

## <a name="next-steps"></a>Další kroky

- [Použití setjmp nebo longjmp v C++ programech](../cpp/using-setjmp-longjmp.md)

  Přečtěte si další informace o použití `setjmp` a `longjmp` v C++ programech.

- [Ošetření strukturovaných výjimek v C++](../cpp/exception-handling-differences.md)

  Podívejte se na příklady způsobů, jak můžete C++ použít ke zpracování strukturovaných výjimek.

## <a name="see-also"></a>Viz také:

[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md)
