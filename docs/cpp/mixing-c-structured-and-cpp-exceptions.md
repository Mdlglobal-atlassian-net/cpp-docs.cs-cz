---
title: Kombinace jazyka C (strukturované) a výjimky jazyka C++
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 94d6dc249cb130aaf09d3202b9e8f437d00a9597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548199"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Kombinace jazyka C (strukturované) a výjimky jazyka C++

Pokud chcete zapsat přenositelný kód, není doporučeno používat zpracování strukturovaných výjimek (SEH) v programu v jazyce C++. Však můžete někdy chtít zkompilovat pomocí [/EHa](../build/reference/eh-exception-handling-model.md) spojit strukturované výjimky a zdrojový kód jazyka C++ a někdy třeba zařízení pro práci s oběma druhy výjimek. Protože obslužná rutina strukturované výjimky nemá žádný koncept objektů ani typových výjimek, nemůže zpracovat výjimky vyvolané z kódu jazyka C++. Nicméně C++ **catch** obslužné rutiny strukturované výjimky zpracovat mohou. Syntaxe zpracování výjimek jazyka C++ (**zkuste**, **throw**, **catch**) neakceptuje kompilátor jazyka C, ale syntaxe zpracování strukturovaných výjimek (**definovaný blok __try**, **__except**, **__finally**) je podporována kompilátorem jazyka C++.

Zobrazit [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) informace o tom, jak zpracování strukturovaných výjimek jako výjimek jazyka C++.

Jsou-li zkombinovány strukturované a výjimky jazyka C++, mějte na paměti těchto potenciálních problémů:

- Výjimky jazyka C++ a strukturované výjimky nelze kombinovat v rámci stejné funkce.

- Obslužné rutiny ukončení (**__finally** bloky) jsou provedeny vždy, i v případě odvíjení po vyvolání výjimky.

- Zpracování výjimek jazyka C++ může zachytit a zachovat sémantiku odvíjení ve všech modulech zkompilovaných pomocí [/EH](../build/reference/eh-exception-handling-model.md) – možnosti kompilátoru, které umožňují sémantiku odvíjení.

- Mohou existovat situace, ve kterých nejsou funkce destruktoru volány pro všechny objekty. Například pokud se strukturovaná výjimka objeví při pokusu provést volání funkce prostřednictvím ukazatele neinicializované funkce, přičemž tato funkce přijímá jako parametry objekty, které byly vytvořeny před voláním, destruktory tyto objekty nejsou volány během odvíjení zásobníku.

## <a name="next-steps"></a>Další kroky

- [Použití funkcí setjmp a longjmp v programech jazyka C++](../cpp/using-setjmp-longjmp.md)

  Zobrazit další informace týkající se použití `setjmp` a `longjmp` v programech jazyka C++.

- [Ošetření strukturovaných výjimek v C++](../cpp/exception-handling-differences.md)

  Příklady způsobů, jak vám umožní zpracování strukturovaných výjimek jazyka C++.

## <a name="see-also"></a>Viz také:

[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)
