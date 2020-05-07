---
title: Doporučené postupy optimalizace
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328442"
---
# <a name="optimization-best-practices"></a>Doporučené postupy optimalizace

Tento dokument popisuje některé osvědčené postupy pro optimalizaci programů v jazyce C++ v aplikaci Visual Studio.

## <a name="compiler-and-linker-options"></a>Možnosti kompilátoru a linkeru

### <a name="profile-guided-optimization"></a>Optimalizace na základě profilu

Visual Studio podporuje *optimalizaci na základě profilu* (PGO). Tato optimalizace používá data profilu z cvičení provádění instrumentované verze aplikace až po pozdější optimalizaci aplikace. Použití PGO může být časově náročné, takže se nemusí jednat o něco, co používá každý vývojář, ale doporučujeme použít PGO pro finální sestavení vydání produktu. Další informace najdete v tématu [optimalizace na základě profilu](profile-guided-optimizations.md).

Kromě toho je *optimalizace celého programu* (také ví, že se jedná o generování kódu při propojování) a vylepšily se optimalizace **/O1** a **/O2** . Obecně platí, že aplikace kompilovaná s jednou z těchto možností bude rychlejší než stejná aplikace kompilována s dřívějším kompilátorem.

Další informace najdete v tématech [/GL (celková optimalizace programu)](reference/gl-whole-program-optimization.md) a [/O1,/O2 (minimalizujte velikost, Maximalizujte rychlost)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Jakou úroveň optimalizace použít

Pokud je to možné, konečné buildy vydaných verzí by se měly kompilovat s optimalizacemi na základě profilu. Pokud není možné sestavovat pomocí PGO, ať už z důvodu nedostatečné infrastruktury pro spouštění instrumentovaná sestavení nebo nemáte přístup k scénářům, doporučujeme sestavování s optimalizací celé aplikace.

Přepínač **/Gy** je také velmi užitečný. Generuje samostatné COMDAT pro každou funkci, takže linker větší flexibility při odebrání neodkazované sekvence COMDAT a COMDAT skládání. Jediným nevýhodou pro použití **/Gy** je to, že může způsobit problémy při ladění. Proto se obvykle doporučuje použít. Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](reference/gy-enable-function-level-linking.md).

Pro propojení v 64 prostředích doporučujeme použít možnost linkeru **/OPT: REF, ICF** a v 32 prostředích **/OPT: ref** . Další informace najdete v tématu [/opt (optimalizace)](reference/opt-optimizations.md).

Doporučuje se také vytvořit symboly ladění i s optimalizovanými sestaveními vydaných verzí. Neovlivňuje generovaný kód a díky tomu je mnohem jednodušší ladit aplikaci, pokud je potřeba.

### <a name="floating-point-switches"></a>Přepínače s plovoucí desetinnou čárkou

Možnost kompilátoru **/op** byla odebrána a byly přidány následující čtyři možnosti kompilátoru týkající se optimalizace plovoucí desetinné čárky:

|||
|-|-|
|**/FP: přesný**|Toto je výchozí doporučení a mělo by se používat ve většině případů.|
|**/FP: Fast**|Doporučuje se, pokud je výkon nejvyšší důležitosti, například ve hrách. Výsledkem bude nejrychlejší výkon.|
|**/FP: Strict**|Doporučuje se, pokud jsou požadovány přesné výjimky s plovoucí desetinnou čárkou a chování IEEE. Výsledkem bude nejpomalejší výkon.|
|**/FP: s výjimkou [-]**|Lze použít ve spojení s **/FP: Strict** nebo **/FP: přesný**, ale ne **/FP: Fast**.|

Další informace najdete v tématu [/FP (určení chování s plovoucí](reference/fp-specify-floating-point-behavior.md)desetinnou čárkou).

## <a name="optimization-declspecs"></a>Declspecs optimalizace

V této části se podíváme na dva declspecs, které se dají použít v programech pro zvýšení `__declspec(restrict)` výkonu `__declspec(noalias)`: a.

Declspec `restrict` se dá použít jenom pro deklarace funkce, které vracejí ukazatel, jako je například.`__declspec(restrict) void *malloc(size_t size);`

`restrict` Declspec se používá ve funkcích, které vracejí ukazatele s nealiasem. Toto klíčové slovo se používá pro implementaci běhové knihovny jazyka C `malloc` , protože nikdy nevrátí hodnotu ukazatele, která je již v aktuálním programu používána (Pokud neprovádíte něco neoprávněně, například při použití paměti po uvolnění paměti).

`restrict` Declspec poskytuje kompilátoru více informací pro provádění optimalizací kompilátoru. Jedním z nejzávažných věcí pro kompilátor pro určení je to, které ukazatele aliasují jiné ukazatele a využívají tyto informace významně pomáhají kompilátorům.

Je potřeba upozornit na to, že se jedná o příslib kompilátoru, ne o něco, co kompilátor ověří. Pokud váš program používá tuto `restrict` declspec nevhodným způsobem, váš program pravděpodobně nemá správné chování.

Další informace najdete v tématu [omezení](../cpp/restrict.md).

`noalias` Declspec se také používá jenom pro funkce a označuje, že funkce je částečně čistá. Částečně čistá funkce je ta, která odkazuje nebo upravuje pouze lokální hodnoty, argumenty a přesměrování první úrovně argumentů. Tento declspec je příslib kompilátoru, a pokud funkce odkazuje na Globals nebo na druhé úrovni argumentů ukazatelů, kompilátor může vygenerovat kód, který aplikaci přeruší.

Další informace najdete v tématu [jiné](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Direktivy pragma optimalizace

K dispozici je také několik užitečných direktiv pragma pro pomoc s optimalizací kódu. První z nich se `#pragma optimize`zabývá:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Tato direktiva pragma umožňuje nastavit danou úroveň optimalizace na základě funkcí. To je ideální pro případy, kdy dojde k chybě vaší aplikace, když je daná funkce zkompilována s optimalizací. Tuto možnost můžete použít k vypnutí optimalizace pro jednu funkci:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Další informace najdete v tématu věnovaném [optimalizaci](../preprocessor/optimize.md).

Vkládání je jedním z nejdůležitějších optimalizací, které kompilátor provádí, a tady hovoříme o několika direktivách pragma, které vám pomůžou toto chování upravit.

`#pragma inline_recursion`je užitečné pro určení, zda chcete, aby aplikace mohla být vložena do rekurzivního volání. Ve výchozím nastavení je vypnutý. V případě omezené rekurze malých funkcí, které můžete zapnout. Další informace najdete v tématu [inline_recursion](../preprocessor/inline-recursion.md).

Další užitečnou direktivou pragma pro omezení hloubky vkládání `#pragma inline_depth`je. To je obvykle užitečné v situacích, kdy se snažíte omezit velikost programu nebo funkce. Další informace najdete v tématu [inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict a \__assume

V aplikaci Visual Studio existuje několik klíčových slov, které mohou přispět k výkonu: [__restrict](../cpp/extension-restrict.md) a [__assume](../intrinsics/assume.md).

Nejdřív by se měla poznamenat, `__restrict` že `__declspec(restrict)` a jsou dvě různé věci. I když se trochu vztahují, jejich sémantika se liší. `__restrict`je kvalifikátor typu, jako `const` nebo `volatile`, ale výhradně pro typy ukazatelů.

Ukazatel, který je upraven pomocí `__restrict` , je označován jako *ukazatel __restrict*. Ukazatel __restrict je ukazatel, ke kterému lze přistupovat pouze prostřednictvím \_ukazatele _restrict. Jinými slovy, jiný ukazatel nelze použít pro přístup k datům, na která ukazuje ukazatel \__restrict.

`__restrict`může se jednat o výkonný nástroj pro optimalizaci Microsoft C++, ale používejte ho s velkou opatrností. Při nesprávném použití může Optimalizátor provést optimalizaci, která by přerušila vaši aplikaci.

`__restrict` Klíčové slovo nahrazuje přepínač **/OA** z předchozích verzí.

Pomocí `__assume`nástroje může vývojář říct kompilátoru, aby vyvedl předpoklady o hodnotě některé proměnné.

Například `__assume(a < 5);` instruuje Optimalizátor, který na tomto řádku kódu je proměnná `a` menší než 5. Znovu se jedná o příslib kompilátoru. Pokud `a` je v tomto okamžiku v programu skutečně 6, pak chování programu po optimalizaci kompilátoru nemusí být to, co byste očekávali. `__assume`je nejužitečnější před přepínat příkazy nebo podmíněnými výrazy.

Existují určitá omezení `__assume`. Jako první, `__restrict`podobně jako, je pouze návrh, takže kompilátor je zdarma ignorovat. V `__assume` současné době funguje pouze s proměnnými nerovnosti před konstantami. Nešíří tak symbolické nerovnosti, například Předpokládejme (a < b).

## <a name="intrinsic-support"></a>Vnitřní podpora

Vnitřní objekty jsou volání funkcí, kde má kompilátor vnitřní znalosti o volání a spíše než volání funkce v knihovně, vygeneruje kód pro tuto funkci. Hlavičkový soubor \<intrin. h> obsahuje všechny dostupné vnitřní funkce pro každou z podporovaných hardwarových platforem.

Vnitřní prvky poskytují programátorovi možnost přejít hluboko do kódu bez nutnosti používat sestavení. Použití vnitřních objektů přináší několik výhod:

- Váš kód je lépe přenosný. Několik vnitřních objektů je dostupných na více architekturách procesoru.

- Čtení kódu je snazší, protože kód je stále napsán v jazyce C/C++.

- Váš kód získá výhodu optimalizace kompilátoru. Jak je kompilátor lepší, zlepšuje se generování kódu pro vnitřní objekty.

Další informace najdete v tématu [vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Výjimky

Došlo k dosažení výkonu spojených s používáním výjimek. Některá omezení jsou představena při použití bloků try, které brání kompilátoru v provádění určitých optimalizací. Na platformách x86 existuje další snížení výkonu z bloků try z důvodu dalších informací o stavu, které musí být generovány při provádění kódu. Na 64 64bitových platformách testovaný blok nesnižuje výkon, ale jakmile je vyvolána výjimka, proces nalezení obslužné rutiny a odvinutí zásobníku může být nákladný.

Proto se doporučuje vyhnout se zavlečení bloku try/catch do kódu, který ho skutečně nepotřebuje. Pokud je nutné použít výjimky, použijte synchronní výjimky, pokud je to možné. Další informace naleznete v tématu [strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Nakonec vyvolejte výjimky pouze pro výjimečné případy. Použití výjimek pro obecný tok řízení způsobí, že dojde ke zhoršení výkonu.

## <a name="see-also"></a>Viz také

- [Optimalizace kódu](optimizing-your-code.md)
