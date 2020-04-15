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

Tento dokument popisuje některé osvědčené postupy pro optimalizaci aplikací jazyka C++ v sadě Visual Studio.

## <a name="compiler-and-linker-options"></a>Možnosti kompilátoru a propojovacího zařízení

### <a name="profile-guided-optimization"></a>Optimalizace s asistencí profilu

Visual Studio podporuje *optimalizaci s asistencí profilu* (PGO). Tato optimalizace používá data profilu z trénovacích spuštění instrumentované verze aplikace k pozdější optimalizaci aplikace. Použití PGO může být časově náročné, takže to nemusí být něco, co používá každý vývojář, ale doporučujeme používat PGO pro konečnou verzi produktu. Další informace naleznete v [tématu Optimalizace s asistencí profilu](profile-guided-optimizations.md).

Kromě toho byla vylepšena *optimalizace celého programu* (také se označuje jako generování kódu doby propojení) a optimalizace **/O1** a **/O2.** Obecně platí, že aplikace zkompilovaná s jednou z těchto možností bude rychlejší než stejná aplikace zkompilovaná s dřívějším kompilátorem.

Další informace naleznete v [tématech /GL (Optimalizace celého programu)](reference/gl-whole-program-optimization.md) a [/O1, /O2 (Minimalizovat velikost, Maximalizovat rychlost)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Jakou úroveň optimalizace použít

Pokud je to možné, konečná verze sestavení by měla být kompilována s optimalizací s asistencí profilu. Pokud není možné vytvářet s PGO, ať už z důvodu nedostatečné infrastruktury pro spuštění instrumentovaných sestavení nebo nemají přístup ke scénářům, pak doporučujeme sestavení s optimalizace celého programu.

Přepínač **/Gy** je také velmi užitečný. Generuje samostatný COMDAT pro každou funkci, dává propojovacímu systému větší flexibilitu, pokud jde o odebrání neodkazovaných COMDATs a skládání COMDAT. Jedinou nevýhodou použití **/Gy** je, že může způsobit problémy při ladění. Proto se obecně doporučuje používat. Další informace naleznete v tématu [/Gy (Enable Function-Level Linking)](reference/gy-enable-function-level-linking.md).

Pro propojení v 64bitových prostředích se doporučuje použít možnost propojovacího systému **/OPT:REF,ICF** a v 32bitových prostředích **/OPT:REF.** Další informace naleznete v tématu [/OPT (Optimalizace)](reference/opt-optimizations.md).

Důrazně se také doporučuje generovat ladicí symboly, a to i s optimalizovanými sestaveními verzí. Nemá vliv na generovaný kód a usnadňuje ladění aplikace, v případě potřeby.

### <a name="floating-point-switches"></a>Přepínače s plovoucí desetinnou desetinnou tázkami

Možnost kompilátoru **/Op** byla odebrána a byly přidány následující čtyři možnosti kompilátoru zabývající se optimalizací s plovoucí desetinnou desetinnou hmezimnou:

|||
|-|-|
|**/fp:přesné**|Toto je výchozí doporučení a ve většině případů by mělo být použito.|
|**/fp:rychlé**|Doporučeno, pokud je výkon nanejvýš důležitý, například ve hrách. Výsledkem bude nejrychlejší výkon.|
|**/fp:striktní**|Doporučuje se, pokud je požadováno přesné výjimky s plovoucí desetinnou desetinnou a chování IEEE. Výsledkem bude nejpomalejší výkon.|
|**/fp:kromě[-]**|Lze použít ve spojení s **/fp:strict** nebo **/fp:precise**, ale ne **/fp:fast**.|

Další informace naleznete v tématu [/fp (Zadat chování s plovoucí desetinnou tázkem).](reference/fp-specify-floating-point-behavior.md)

## <a name="optimization-declspecs"></a>Optimalizace declspecs

V této části se podíváme na dva declspecs, které `__declspec(restrict)` `__declspec(noalias)`mohou být použity v programech na pomoc výkonu: a .

Declspec `restrict` lze použít pouze pro deklarace funkce, které vracejí ukazatel, například`__declspec(restrict) void *malloc(size_t size);`

Declspec se `restrict` používá u funkcí, které vracejí nealiased ukazatele. Toto klíčové slovo se používá pro `malloc` implementaci knihovny C-Runtime, protože nikdy nevrátí hodnotu ukazatele, která je již používána v aktuálním programu (pokud neděláte něco nezákonného, například použití paměti po uvolnění).

Declspec `restrict` poskytuje kompilátoru další informace pro provádění optimalizace kompilátoru. Jednou z nejtěžších věcí pro kompilátor určit, je jaké ukazatele alias jiné ukazatele a pomocí těchto informací výrazně pomáhá kompilátoru.

Stojí za to zdůraznit, že se jedná o slib kompilátoru, nikoli něco, co kompilátor ověří. Pokud program používá `restrict` tento declspec nevhodně, může mít program nesprávné chování.

Další informace naleznete v tématu [omezení](../cpp/restrict.md).

Declspec `noalias` je také použita pouze pro funkce a označuje, že funkce je poločistá funkce. Poločistá funkce je funkce, která odkazuje nebo upravuje pouze místní, argumenty a dereference argumentů první úrovně. Tento declspec je příslib kompilátoru a pokud funkce odkazuje na globální nebo druhé úrovně indirections argumentů ukazatele pak kompilátor může generovat kód, který přeruší aplikaci.

Další informace naleznete v tématu [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Optimalizace pragmas

Existuje také několik užitečných pragmas pro pomoc optimalizovat kód. První, o které budeme `#pragma optimize`diskutovat, je:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Tento pragma umožňuje nastavit danou úroveň optimalizace na základě funkce po funkci. To je ideální pro ty vzácné případy, kdy dojde k chybě aplikace, když je daná funkce kompilována s optimalizací. Pomocí této funkce můžete vypnout optimalizace pro jednu funkci:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Další informace naleznete v [tématu optimalizace](../preprocessor/optimize.md).

Vkládání je jedním z nejdůležitějších optimalizací, které kompilátor provádí a zde mluvíme o pár pragmas, které pomáhají změnit toto chování.

`#pragma inline_recursion`je užitečné pro určení, zda chcete, aby aplikace mohla vkládat rekurzivní volání. Ve výchozím nastavení je vypnutý. Pro mělké rekurze malých funkcí můžete zapnout. Další informace naleznete [v tématu inline_recursion](../preprocessor/inline-recursion.md).

Dalším užitečným pragma pro omezení `#pragma inline_depth`hloubky vkládání je . To je obvykle užitečné v situacích, kdy se pokoušíte omezit velikost programu nebo funkce. Další informace naleznete [v tématu inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict \_a _assume

V sadě Visual Studio existuje několik klíčových slov, která mohou pomoci s výkonem: [__restrict](../cpp/extension-restrict.md) a [__assume](../intrinsics/assume.md).

Za prvé, je `__restrict` třeba `__declspec(restrict)` poznamenat, že a jsou dvě různé věci. Zatímco oni jsou poněkud příbuzné, jejich sémantika jsou různé. `__restrict`je kvalifikátor typu, jako `const` nebo `volatile`, ale výhradně pro typy ukazatelů.

Ukazatel, který je `__restrict` změněn s se označuje jako *ukazatel __restrict*. Ukazatel __restrict je ukazatel, ke kterému lze \_přistupovat pouze prostřednictvím ukazatele _restrict. Jinými slovy jiný ukazatel nelze použít pro přístup \_k datům odkazuje ukazatel _restrict.

`__restrict`může být výkonný nástroj pro optimalizátor Microsoft C++, ale používejte jej s velkou péčí. Pokud je použit nesprávně, optimalizátor může provést optimalizaci, která by přerušila vaši aplikaci.

Klíčové `__restrict` slovo nahradí přepínač **/Oa** z předchozích verzí.

S `__assume`, může vývojář říct kompilátoru, aby předpoklady o hodnotě některé proměnné.

Například `__assume(a < 5);` říká optimalizátoru, že `a` na tomto řádku kódu je proměnná menší než 5. Opět je to slib kompilátoru. Pokud `a` je skutečně 6 v tomto bodě v programu pak chování programu po kompilátoru optimalizoval nemusí být to, co byste očekávali. `__assume`je nejužitečnější před switch příkazy a/nebo podmíněné výrazy.

Existují určitá omezení `__assume`. Za prvé, jako `__restrict`, je to jen návrh, takže kompilátor je zdarma ignorovat. Také `__assume` v současné době pracuje pouze s proměnnými nerovnosti proti konstantám. Nešíří symbolické nerovnosti, například assume(a < b).

## <a name="intrinsic-support"></a>Jiskrová podpora

Vnitřní jsou volání funkcí, kde kompilátor má vnitřní znalosti o volání a místo volání funkce v knihovně, vydává kód pro tuto funkci. Soubor \<záhlaví intrin.h> obsahuje všechny dostupné vnitřní objekty pro každou z podporovaných hardwarových platforem.

Vnitřní objekty dávají programátorovi možnost přejít hluboko do kódu bez nutnosti použití sestavení. Existuje několik výhod pro použití vnitřních?

- Váš kód je přenosnější. Některé vnitřní objekty jsou k dispozici na více architektur procesoru.

- Váš kód je čitelnější, protože kód je stále zapsán v jazyce C/C++.

- Váš kód získá výhodu optimalizace kompilátoru. Jak se kompilátor zlepšuje, generování kódu pro vnitřní objekty se zlepšuje.

Další informace naleznete [v tématu Compiler Intrinsics](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Výjimky

Je výkon přístupů spojené s pomocí výjimky. Některá omezení jsou zavedeny při použití try bloky, které brání kompilátoru provádět určité optimalizace. Na platformách x86 je další snížení výkonu z try bloků z důvodu další informace o stavu, které musí být generovány během provádění kódu. Na 64bitových platformách try bloky nesnižují výkon tolik, ale jakmile je vyvolána výjimka, proces hledání obslužné rutiny a odvíjení zásobníku může být nákladné.

Proto se doporučuje vyhnout se zavedení try/catch bloky do kódu, který není opravdu potřebuje. Pokud je nutné použít výjimky, použijte synchronní výjimky, pokud je to možné. Další informace naleznete [v tématu Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Nakonec vyvolat výjimky pouze pro výjimečné případy. Použití výjimek pro obecný tok řízení pravděpodobně způsobí, že dojde k utrpět výkon.

## <a name="see-also"></a>Viz také

- [Optimalizace kódu](optimizing-your-code.md)
