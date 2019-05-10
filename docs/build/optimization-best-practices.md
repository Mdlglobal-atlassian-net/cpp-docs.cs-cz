---
title: Doporučené postupy optimalizace
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 42178f8326def78f37bfcc905b96f37c7fc3affc
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220265"
---
# <a name="optimization-best-practices"></a>Doporučené postupy optimalizace

Tento dokument popisuje některé osvědčené postupy pro optimalizaci C++ programů v sadě Visual Studio.

## <a name="compiler-and-linker-options"></a>Kompilátor a možnosti Linkeru

### <a name="profile-guided-optimization"></a>Optimalizace na základě profilu

Visual Studio podporuje *profilováním řízená optimalizace* (PGO). Tato optimalizace se používá profil data z školení spuštění instrumentované verze této aplikace Centrum umožňující prosazovat novější optimalizace aplikace. Použití PGO může být časově náročné, proto to nemusí být něco, co každý vývojář používá, ale doporučujeme používat PGO pro sestavení konečné verze produktu. Další informace najdete v tématu [Profile-Guided optimalizace](profile-guided-optimizations.md).

Kromě toho *optimalizace celého programu* (také ví jako generování kódu při propojování) a **/O1** a **/O2** byly vylepšeny optimalizace. Obecně platí aplikace kompilována s některou z těchto možností proběhne rychleji než stejnou aplikaci zkompilované s starší kompilátoru.

Další informace najdete v tématu [/GL (optimalizace celého programu)](reference/gl-whole-program-optimization.md) a [/O1, / O2 (minimalizovat velikost, maximální rychlost)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Jaké úroveň optimalizace použití

Pokud je to možné vydání finální verze sestavení by měl být zkompilován pomocí optimalizace na základě profilu. Pokud není možné vytvořit pomocí PGO, ať už kvůli nedostatku infrastrukturu pro spuštění instrumentované sestavení nebo nemají přístup ke scénářům, doporučujeme sestavování s využitím optimalizace celého programu.

**/Gy** přepínač je také velmi užitečné. Generuje samostatné COMDAT pro každou funkci, linker poskytuje větší flexibilitu při rozhodování o odebrání neodkazovaných sekvencí Comdat a sekvencí COMDAT skládání. Pouze nevýhodou použití **/Gy** je, že může způsobit problémy při ladění. Proto se obecně doporučuje používat. Další informace najdete v tématu [/Gy (povolení funkce propojení na úrovni)](reference/gy-enable-function-level-linking.md).

Propojení v prostředích 64-bit, doporučuje se použít **OPT, ICF** – možnost linkeru a v prostředích s 32-bit **OPT** se doporučuje. Další informace najdete v tématu [/OPT (optimalizace)](reference/opt-optimizations.md).

Také důrazně se doporučuje generovat symboly ladění, dokonce i u sestavení pro vydání optimalizované. Neovlivňuje generovaný kód a umožňuje snadněji ladit aplikaci, pokud mnoho musí být.

### <a name="floating-point-switches"></a>Přepínače s plovoucí desetinnou čárkou

**/Op** – možnost kompilátoru jsme odebrali a přidali následující čtyři možnosti kompilátoru týkající se plovoucí bodu optimalizace:

|||
|-|-|
|**/ FP: precise**|Toto je výchozí doporučení a byste měli použít ve většině případů.|
|**Fast**|Doporučuje, pokud výkon je naprosto, například ve hrách. Výsledkem bude nejrychlejší výkon.|
|**/ FP: strict**|Doporučené if přesné výjimky s plovoucí desetinnou čárkou a IEEE požadované chování. Výsledkem bude nejpomalejší výkonu.|
|**/fp:except[-]**|Můžete použít ve spojení s **/FP: strict** nebo **/FP: precise**, ale ne **Fast**.|

Další informace najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Optimalizace declspecs

V této části se podíváme na dvou declspecs, které umožňuje v aplikacích vám pomůže zvýšit výkon: `__declspec(restrict)` a `__declspec(noalias)`.

`restrict` Declspec může používat jedině pro deklarace funkce, které vrací ukazatel, jako například `__declspec(restrict) void *malloc(size_t size);`

`restrict` Declspec je používat pro funkce, které vracejí ukazatele kapitoly. Toto klíčové slovo se používá pro implementaci modulu C Runtime Library `malloc` protože nikdy vrátí hodnotu ukazatele, který se už používá v aktuální aplikaci (Pokud děláte něco neplatné, jako je třeba použití paměti, jakmile byl uvolněn).

`restrict` Declspec obsahuje kompilátor bližší informace pro provedení optimalizace kompilátoru. Jedna z těch nejtěžších věcí pro kompilátoru k určení jaké ukazatele alias dalšími ukazateli, a výrazně pomocí těchto informací vám může kompilátor.

To je zmínku, že se jedná o příslib, kterým v kompilátoru, není něco, co kompilátor ověří. Pokud program používá tento `restrict` declspec nesprávně, váš program může vést k nesprávnému chování.

Další informace najdete v tématu [omezit](../cpp/restrict.md).

`noalias` Declspec platí pouze pro funkce a označuje, že funkce je částečně čistě funkce. Částečně čistě funkce je ten, který odkazuje na nebo upravuje pouze lokální proměnné, argumenty a nepřímá argumentů. Tato declspec je příslib z k kompilátor a pokud globals odkazuje na funkci nebo nepřímé odkazy druhé úrovně argumenty ukazatele pak kompilátor může vygenerovat kód, který přeruší aplikace.

Další informace najdete v tématu [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Optimalizace pragmas

Existuje také několik užitečných direktivy pragma pomáhá optimalizovat kód. Tomu se budeme podrobněji první z nich je `#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Tato direktiva pragma umožňuje nastavit úroveň daného optimalizace na základě funkce funkce. To je ideální pro těch výjimečných případech, kdy aplikace ukončí při danou funkci je zkompilován s optimalizací. Může být využit k vypnutí možnosti optimalizace pro jednu funkci:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Další informace najdete v tématu [optimalizovat](../preprocessor/optimize.md).

Vkládání je jedním z nejdůležitějších optimalizace, které provádí kompilátor a tady budeme mluvit o pár direktiv pragma, které pomůžou toto chování upravit.

`#pragma inline_recursion` je užitečné pro určení, zda chcete aplikaci, která bude moct vložené rekurzivní volání. Ve výchozím nastavení je vypnuté. Bez podstruktury rekurze malé funkce můžete zapnout. Další informace najdete v tématu [inline_recursion](../preprocessor/inline-recursion.md).

Další užitečné – Direktiva pragma pro omezení hloubku vkládání je `#pragma inline_depth`. To je obvykle užitečné v situacích, kdy se snažíte omezení velikosti programu nebo funkce. Další informace najdete v tématu [inline_depth](../preprocessor/inline-depth.md).

## <a name="restrict-and-assume"></a>Kvalifikátor __restrict a \__assume

Existuje několik klíčových slov v sadě Visual Studio, který vám pomůže výkonu: [kvalifikátor __restrict](../cpp/extension-restrict.md) a [__assume](../intrinsics/assume.md).

Nejprve je třeba poznamenat, že `__restrict` a `__declspec(restrict)` jsou dvě různé věci. Při nich do jisté míry se vztahují, se liší jejich sémantiku. `__restrict` Kvalifikátor typu, jako je třeba je `const` nebo `volatile`, ale výhradně pro typy ukazatelů.

Ukazatel, který se mění `__restrict` se označuje jako *kvalifikátor __restrict ukazatel*. __Restrict ukazatel je ukazatel, který je přístupný pouze prostřednictvím \__restrict ukazatele. Jinými slovy, jinému ukazateli nelze použít pro přístup k datům, na které odkazují \__restrict ukazatele.

`__restrict` může být výkonný nástroj pro Microsoft C++ optimalizace, ale jeho použití s pozornost. Pokud použili nesprávně, optimalizátor může provádět optimalizace, která by se narušil vaší aplikace.

`__restrict` Nahradí – klíčové slovo **/Oa** přepnout z předchozích verzí.

S `__assume`, Vývojář můžete říct, kompilátor, aby byl předpoklady o hodnotě některé proměnné.

Například `__assume(a < 5);` říká Optimalizátor, který na tomto řádku kódu proměnné `a` je menší než 5. To je opět příslib, kterým kompilátor. Pokud `a` je ve skutečnosti 6 v tuto chvíli v programu, pak chování programu po má kompilátor optimalizovat nemusí být co byste očekávali. `__assume` je nejužitečnější před příkazů přepínače a/nebo podmíněné výrazy.

Existují některá omezení, která `__assume`. Nejprve, jako jsou `__restrict`, je pouze návrh, kompilátor je zdarma ignorujte. Navíc `__assume` v současné době používá pouze proměnné nerovností proti konstanty. Symbolické nerovností nešíří například assume(a < b).

## <a name="intrinsic-support"></a>Vnitřní podporu

Vnitřní objekty jsou funkce volá kompilátor má vnitřní znalosti o volání, kde místo volání funkce v knihovně, se generuje kód pro tuto funkci. Soubor hlaviček \<intrin.h > obsahuje všechny vnitřní objekty dostupné pro každou z platforem podporovaných hardwaru.

Vnitřní objekty umožnit programátor zanořovat hluboko do kódu bez nutnosti použití sestavení. Existuje více výhod použití vnitřních objektů:

- Je větší přenositelnost kódu. Některé vnitřní objekty jsou k dispozici na několika architektur procesoru.

- Je váš kód lépe čitelný, protože kód je stále napsané v jazyce C/C++.

- Váš kód získá výhodou optimalizace kompilátoru. Protože kompilátor získá lepší, lepší generování kódu pro vnitřní objekty.

Další informace najdete v tématu [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Výjimky

Výkon je dosaženo spojených s použitím výjimky. Při použití bloky try, které kompilátor bránit v provádění některé optimalizace zavedení určitá omezení. Na x86 zkuste platformy, kterým je snížení výkonu další z bloků z důvodu informace o dalších stavu, který musí být vygenerován při provádění kódu. Na 64bitových platformách, zkuste bloky nezhorší výkon tolik, ale když je vyvolána výjimka, proces hledání obslužné rutiny a odvíjení zásobníku může být nákladné.

Proto se doporučuje Vyhýbejte se bloky try/catch do kódu, který nepotřebuje skutečně ho. Pokud je nutné použít výjimky, pokud je to možné použijte synchronní výjimky. Další informace najdete v tématu [strukturovaného zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

A konečně vyvolejte výjimky pro pouze výjimečných případech. Použití výjimek pro tok řízení obecné budou pravděpodobně trpět výkon.

## <a name="see-also"></a>Viz také:

- [Optimalizace kódu](optimizing-your-code.md)
