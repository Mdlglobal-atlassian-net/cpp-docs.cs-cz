---
title: Doporučené postupy optimalizace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e869a12635117f37f32fad3dcfdd38ed45d401e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="optimization-best-practices"></a>Doporučené postupy optimalizace
Tento dokument popisuje některé z osvědčených postupů pro optimalizaci v jazyce Visual C++. Jsou popsané v následujících tématech:  
  
-   Kompilátor a možnosti Linkeru  
  
    -   optimalizace na základě profilu  
  
    -   Kterou úroveň optimalizace mám použít?  
  
    -   Plovoucí bodu přepínače  
  
-   Optimalizace Declspecs  
  
-   Optimalizace Pragmas  
  
-   __restrict a \__assume  
  
-   Vnitřní podpory  
  
-   Výjimky  
  
## <a name="compiler-and-linker-options"></a>Kompilátor a možnosti Linkeru  
  
### <a name="profile-guided-optimization"></a>optimalizace na základě profilu  
 Visual C++ podporuje optimalizace na základě profilu (PGO). Tato optimalizace používá data profilu z posledních spuštěních instrumentovaného verze aplikace na novější optimalizace aplikace jednotek. Pomocí PGO může být časově náročné, proto nemusí být něco, co každý vývojář používá, ale doporučujeme používat PGO pro sestavení finální verzi produktu. Další informace najdete v tématu [Profile-Guided optimalizace](../../build/reference/profile-guided-optimizations.md).  
  
 Kromě toho optimalizace celého programu (také zná jako vytvoření kódu v době odkaz) a **/O1** a **/O2** optimalizace se zlepšila. Obecně platí aplikace, kompilovat s některou z těchto možností bude rychlejší než stejná aplikace, kompilovat s dřívější kompilátoru.  
  
 Další informace najdete v tématu [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md) a [/O1, / O2 (velikost minimalizovat, maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).  
  
### <a name="which-level-of-optimization-should-i-use"></a>Kterou úroveň optimalizace mám použít?  
 Pokud je to možné finální verzi sestavení má kompilovat s optimalizace na základě profilu. Pokud není možné vytvořit s PGO, zda z důvodu nedostatečných infrastruktury pro spuštění instrumentovaného sestavení nebo nemá přístup k scénáře, doporučujeme sestavení s optimalizace celého programu.  
  
 **/Gy** přepínač je velmi užitečné. Vygeneruje samostatné sekvence COMDAT pro jednotlivé funkce poskytnutí linkeru větší flexibilitu při rozhodování o odebrání neodkazované sekvence COMDAT a COMDATs skládání. Pouze nevýhodou použití **/Gy** je, že může mít menší vliv na čase vytvoření buildu. Proto obecně doporučujeme používat. Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md).  
  
 Propojení v prostředích 64-bit, doporučuje se použít **/OPT:REF, bránou Firewall** – možnost linkeru a v prostředích s 32-bit **/OPT:REF** se doporučuje. Další informace najdete v tématu [/OPT (optimalizace)](../../build/reference/opt-optimizations.md).  
  
 Také důrazně doporučujeme pro generování symboly ladění, i když optimalizované verzi sestavení. Ho nebude ovlivňuje generovaný kód, a umožňuje snazší ladění aplikace, pokud mnoho musí být.  
  
### <a name="floating-point-switches"></a>Plovoucí bodu přepínače  
 **/Op** – možnost kompilátoru byla odebrána, a byly přidány následující čtyři možnosti kompilátoru zabývajících se plovoucí optimalizace bodu:  
  
|||  
|-|-|  
|**/FP: přesné**|Toto je výchozí doporučení a by měl být použit ve většině případů.|  
|**/FP:Fast**|Doporučuje se, pokud výkon je nesmírně důležité, například v hry. Výsledkem bude nejrychlejší výkon.|  
|**/FP: striktní**|Doporučené v případě přesné výjimky s plovoucí desetinnou čárkou a IEEE chování žádoucí. Výsledkem bude nejpomalejší výkon.|  
|**/FP: kromě [-]**|Můžete použít ve spojení s **/fp: striktní** nebo **/fp: přesné**, ale ne **/fp:fast**.|  
  
 Další informace najdete v tématu [/fp (zadejte Floating-Point chování)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
## <a name="optimization-declspecs"></a>Optimalizace Declspecs  
 V této části se podíváme na dva declspecs, které lze v programech, vám pomůže zvýšit výkon: `__declspec(restrict)` a `__declspec(noalias)`.  
  
 `restrict` Declspec lze použít pouze pro deklarace funkcí, které vracejí ukazatele, jako například `__declspec(restrict) void *malloc(size_t size);`  
  
 `restrict` Declspec se používá na funkce, které vrací kapitoly ukazatele. This – klíčové slovo se používá k provedení C Runtime Library `malloc` vzhledem k tomu, že nikdy vrátí ukazatel na hodnotu, která je již používán v aktuálním programem (Pokud nechcete provádět něco neplatné, například pomocí paměti po bylo uvolněno).  
  
 `restrict` Declspec obsahuje kompilátor bližší informace o provádění optimalizace kompilátoru. Jeden z nejtěžší akcí pro kompilátor k určení je co alias ukazatele na další ukazatele a výrazně na základě těchto informací pomáhá kompilátoru.  
  
 Je vhodné odkazující je promise kompilátoru, není něco, co ověří, jestli kompilátoru. Pokud váš program používá toto `restrict` declspec nesprávně, váš program může vést k nesprávnému chování.  
  
 Další informace najdete v tématu [omezit](../../cpp/restrict.md).  
  
 `noalias` Declspec platí jenom k funkcím a označuje, že funkce je polovičním čistou funkci. Polovičním čistý funkce je ten, který odkazuje na nebo upraví pouze místní hodnoty, argumentů a první úrovně indirections argumentů. Tento declspec je promise kompilátoru a pokud funkce odkazuje na globální funkce nebo druhé úrovně indirections ukazatel argumenty pak kompilátor může generovat kód, který dělí aplikace.  
  
 Další informace najdete v tématu [noalias](../../cpp/noalias.md).  
  
## <a name="optimization-pragmas"></a>Optimalizace Pragmas  
 Existují také několik užitečné direktivy pomáháte optimalizace kódu. První z nich probereme je `#pragma optimize`:  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 Tato direktiva pragma umožňuje nastavit úroveň daného optimalizace na základě pomocí funkcí. To se hodí pro tyto výjimečných případech kde vaše aplikace spadne při kompilaci s optimalizací danou funkci. Můžete to použít k vypnutí možnosti optimalizace pro jednu funkci:  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 Další informace najdete v tématu [optimalizovat](../../preprocessor/optimize.md).  
  
 Vložené je jedním z nejdůležitějších optimalizace, které provádí kompilátor a zde mluvíme o několik direktiv pragma, které pomůžou toto chování změnit.  
  
 `#pragma inline_recursion` je užitečné pro určení, zda chcete aplikaci, která bude moct vložené zpětného volání. Ve výchozím nastavení je vypnuté. Pro bez podstruktury rekurze malé funkcí může tuto možnost zapnout. Další informace najdete v tématu [inline_recursion –](../../preprocessor/inline-recursion.md).  
  
 Další užitečné – Direktiva pragma pro omezení hloubka vložené je `#pragma inline_depth`. To je obvykle užitečné v situacích, kde se pokoušíte omezení velikosti programu nebo funkce. Další informace najdete v tématu [inline_depth –](../../preprocessor/inline-depth.md).  
  
## <a name="restrict-and-assume"></a>__restrict a \__assume  
 Existuje několik klíčových slov v jazyce Visual C++, který vám pomůže výkonu: [__restrict](../../cpp/extension-restrict.md) a [__assume](../../intrinsics/assume.md).  
  
 Nejdřív je potřeba poznamenat, `__restrict` a `__declspec(restrict)` dvě různé věci. Při poněkud souvisejí, jejich sémantiku se liší. `__restrict` Kvalifikátor typu, jako je třeba je `const` nebo `volatile`, ale výhradně pro typy ukazatelů.  
  
 Ukazatele, který je změnit, `__restrict` se označuje jako *__restrict ukazatel*. __Restrict ukazatel je ukazatele, který lze přistupovat pouze prostřednictvím \__omezit ukazatel. Jinými slovy, jiné ukazatele nelze použít pro přístup k datům, na kterou odkazuje \__omezit ukazatel.  
  
 `__restrict` může být výkonný nástroj pro Optimalizátor Visual C++, ale jeho použití s pozor. Pokud použili nesprávně, třeba provést Optimalizátor optimalizace, která by rozdělit vaší aplikace.  
  
 `__restrict` Nahrazuje – klíčové slovo **/Oa** přepnout z předchozích verzí.  
  
 S `__assume`, vývojáři mohou oznámení kompilátoru aby předpoklady o hodnotě některé proměnné.  
  
 Například `__assume(a < 5);` informuje okně Optimalizace, u tohoto řádku kódu proměnnou `a` je menší než 5. Toto je znovu promise kompilátoru. Pokud `a` je ve skutečnosti 6 v tomto okamžiku v programu pak chování programu po kompilátor optimalizovala nemusí být co byste očekávali. `__assume` je nejvhodnější před příkazů přepínače nebo podmíněné výrazy.  
  
 Některá omezení pro `__assume`. Nejprve jako `__restrict`, je pouze návrhu, tak, aby kompilátor volné ji ignorovat. Navíc `__assume` aktuálně funguje pouze v proměnné nerovnosti proti konstanty. Symbolický nerovnosti nejsou rozšířena například assume(a < b).  
  
## <a name="intrinsic-support"></a>Vnitřní podpory  
 Vnitřní funkce jsou funkce volá, kde má vnitřní znalosti o volání do kompilátoru a namísto volání funkce v knihovně, se vysílá kód pro tuto funkci. Záhlaví souboru intrin.h nacházející se v \VC\include\intrin.h < Installation_Directory > obsahuje všechny dostupné vnitřní funkce pro všechny tři podporované platformy (x 86, x64 a ARM).  
  
 Vnitřní funkce poskytnout programátorů možnost Přejít o kód bez nutnosti použití sestavení. Existuje několik výhod pomocí vnitřní funkce:  
  
1.  Váš kód je víc přenosného. Řadu vnitřní objekty jsou k dispozici na několika architektury procesoru.  
  
2.  Váš kód je snadněji číst, protože kód je stále napsané v jazyce C/C++.  
  
3.  Váš kód získá výhodou optimalizace kompilátoru. Jak kompilátor získá lepší, zlepšuje generování kódu pro vnitřní objekty.  
  
 Další informace najdete v tématu [vnitřní funkce kompilátoru](../../intrinsics/compiler-intrinsics.md).  
  
## <a name="exceptions"></a>Výjimky  
 Je výkonu podle přidružené k použití výjimek. Při použití bloky try, které bránit kompilátor provedení některých optimalizací, jsou zavedené určitá omezení. Na x86 platformy, které je snížení výkonu další z try – bloky informace o další stav, který musí být generován během provádění kódu. Na 64bitových platformách, zkuste bloky není snížit výkon co nejvíc, ale jakmile je vyvolána výjimka, proces vyhledávání obslužná rutina a unwinding zásobníku může být náročná.  
  
 Proto se doporučuje nedošlo k zavedení bloků try/catch do kódu, který není nutné Opravdu ji. Pokud musíte použít výjimky, pokud je to možné použijte synchronní výjimky. Další informace najdete v tématu [strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Nakonec generování výjimek pro pouze výjimečných případech. Použití výjimek pro tok řízení obecné budou pravděpodobně sníží výkon.  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace kódu](../../build/reference/optimizing-your-code.md)