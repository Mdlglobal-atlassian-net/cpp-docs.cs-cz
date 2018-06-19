---
title: C2700 chyby kompilátoru prostřednictvím C2799 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
dev_langs:
- C++
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cab784c772b8b0faac2bca2bdc3ff7a3465b551
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283855"
---
# <a name="compiler-errors-c2700-through-c2799"></a>C2700 chyby kompilátoru prostřednictvím C2799

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2700](compiler-error-c2700.md)|'*typ*': nemůže být vyvolána (/W4 použijte další informace)|
|[Chyba kompilátoru C2701](compiler-error-c2701.md)|'*funkce*': funkce šablony nebo obecný nemůže být friend místní třídy|
|[Chyba kompilátoru C2702](compiler-error-c2702.md)| __except se nemůže nacházet v bloku ukončení|
|[Chyba kompilátoru C2703](compiler-error-c2703.md)|Neplatný __leave – příkaz|
|[Chyba kompilátoru C2704](compiler-error-c2704.md)|'*funkce*': __va_start vnitřní povoleny pouze v vararg|
|[Chyba kompilátoru C2705](compiler-error-c2705.md)|'*popisek*': Neplatný přechod do "*exception_block*' oboru|
|[Chyba kompilátoru C2706](compiler-error-c2706.md)|Neplatný __except bez odpovídající __try (chybějící '}' v blok __try?)|
|[Chyba kompilátoru C2707](compiler-error-c2707.md)|'*identifikátor*': Chybný kontext pro vnitřní funkce|
|[Chyba kompilátoru C2708](compiler-error-c2708.md)|'*identifikátor*': parametry skutečná délka v bajtech se liší od předchozího volání nebo odkaz|
|[Chyba kompilátoru C2709](compiler-error-c2709.md)|'*identifikátor*': formální parametry Délka v bajtech se liší od předchozí deklarace|
|[Chyba kompilátoru C2710](compiler-error-c2710.md)|'*identifikátor*': ' __declspec (*modifikátor*), lze použít pouze na funkci vrácení ukazatele|
|[Chyba kompilátoru C2711](compiler-error-c2711.md)|'*funkce*': tuto funkci nelze zkompilovat jako spravovaný, zvažte použití #pragma nespravované|
|[Chyba kompilátoru C2712](compiler-error-c2712.md)|nelze použít __try ve funkcích, které vyžadují unwinding objektu|
|[Chyba kompilátoru C2713](compiler-error-c2713.md)|pouze jednu formu povolený na základě funkce zpracování výjimek|
|[Chyba kompilátoru C2714](compiler-error-c2714.md)|alignof(void) není povolen.|
|[Chyba kompilátoru C2715](compiler-error-c2715.md)|'*typ*': nelze vyvolat nebo catch tento typ|
|C2716 chyby kompilátoru|Zastaralé.|
|C2717 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2718](compiler-error-c2718.md)|'*typ*': skutečný parametr s požadovanou zarovnání *číslo* nebude zarovnán|
|[Chyba kompilátoru C2719](compiler-error-c2719.md)|'*parametr*': formální parametr s požadovanou zarovnání *číslo* nebude zarovnán|
|[Chyba kompilátoru C2720](compiler-error-c2720.md)|'*identifikátor*': '*specifikátor*' u členů Neplatný specifikátor třídy úložiště|
|[Chyba kompilátoru C2721](compiler-error-c2721.md)|'*specifikátor*': Neplatný mezi – klíčové slovo operátoru a typ specifikátor třídy úložiště|
|[Chyba kompilátoru C2722](compiler-error-c2722.md)|'::*operátor*': neplatný příkaz následující operátor; použijte ' operátor *operátor*.|
|[Chyba kompilátoru C2723](compiler-error-c2723.md)|'*funkce*': '*specifikátor*' v definici funkce Neplatný specifikátor|
|[Chyba kompilátoru C2724](compiler-error-c2724.md)|'*funkce*":"statická"by se neměla používat na členské funkce, které jsou definované v souboru oboru|
|[Chyba kompilátoru C2725](compiler-error-c2725.md)|'*typ*': nelze vyvolat nebo catch objekt spravované nebo WinRT hodnotou nebo odkazem|
|[Chyba kompilátoru C2726](compiler-error-c2726.md)|'gcnew, může použít pouze pro vytvoření objektu s typem spravované nebo WinRT|
|C2727 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2728](compiler-error-c2728.md)|'*typ*': nativní pole nemůže obsahovat tento typ|
|C2729 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2730](compiler-error-c2730.md)|'*třída*': nemůže být základní třídu sám sebe|
|[Chyba kompilátoru C2731](compiler-error-c2731.md)|'*funkce*': funkce nemohou být přetíženy.|
|[Chyba kompilátoru C2732](compiler-error-c2732.md)|starší specifikace pro specifikaci propojení v rozporu se*funkce*.|
|[Chyba kompilátoru C2733](compiler-error-c2733.md)|'*funkce*': druhé C propojení přetížené funkce není povoleno|
|[Chyba kompilátoru C2734](compiler-error-c2734.md)|'*identifikátor*': 'const' objekt musí inicializovat, pokud není extern|
|[Chyba kompilátoru C2735](compiler-error-c2735.md)|'*– klíčové slovo*' není v specifikátor typu formální parametr povoleno – klíčové slovo|
|[Chyba kompilátoru C2736](compiler-error-c2736.md)|'*– klíčové slovo*' – klíčové slovo není povolena v přetypování|
|C2737 chyby kompilátoru|'*identifikátor*': 'constexpr' objekt musí být inicializován.|
|[Chyba kompilátoru C2738](compiler-error-c2738.md)|' operátor *typ*': je nejednoznačné, nebo není členem '*– třída*.|
|[Chyba kompilátoru C2739](compiler-error-c2739.md)|'*číslo*': explicitní pole spravované nebo WinRT dimenze musí být mezi 1 a 32.|
|C2740 chyby kompilátoru|Hodnota operand '*číslo*"je mimo rozsah"*lower_bound –* - *upper_bound –*.|
|C2741 chyby kompilátoru|rámce příliš velký.|
|C2742 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2743](compiler-error-c2743.md)|'*typ*': nelze catch nativního typu s __clrcall – destruktor nebo kopírovací konstruktor|
|C2744 chyby kompilátoru|'*operátor*' není platný operátor CLR nebo WinRT|
|[Chyba kompilátoru C2745](compiler-error-c2745.md)|'*tokenu*': Tento token nelze převést na identifikátor|
|C2746 chyby kompilátoru|Zastaralé.|
|C2747 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2748](compiler-error-c2748.md)|Vytvoření spravované nebo WinRT pole musí mít velikost pole nebo pole inicializátoru|
|[Chyba kompilátoru C2749](compiler-error-c2749.md)|'*typ*': můžete pouze throw a catch popisovač pro spravované třídy s/clr: safe|
|[Chyba kompilátoru C2750](compiler-error-c2750.md)|'*typ*': nelze použít nové na odkaz na typ; místo toho použijte 'gcnew.|
|[Chyba kompilátoru C2751](compiler-error-c2751.md)|'*parametr*': nemůže být kvalifikovaný název parametru – funkce|
|[Chyba kompilátoru C2752](compiler-error-c2752.md)|'*šablony*': odpovídá více než jeden částečná specializace šablony seznam argumentů|
|[Chyba kompilátoru C2753](compiler-error-c2753.md)|'*šablony*': částečná specializace se nemůže shodovat seznam argumentů pro primární šablony|
|[Chyba kompilátoru C2754](compiler-error-c2754.md)|'*šablony*': částečná specializace nemůže mít parametr závislé bez typu šablony|
|[Chyba kompilátoru C2755](compiler-error-c2755.md)|'*parametr*': parametr není typu částečná specializace musí být jednoduchý identifikátor|
|[Chyba kompilátoru C2756](compiler-error-c2756.md)|'*šablony*': výchozí šablony argumenty nejsou povoleny na částečná specializace|
|[Chyba kompilátoru C2757](compiler-error-c2757.md)|'*identifikátor*': symbol s tímto názvem již existuje, a proto nelze tento název použít jako název oboru názvů|
|[Chyba kompilátoru C2758](compiler-error-c2758.md)|'*člen*': členem typ odkazu musí být inicializován.|
|C2759 chyby kompilátoru|řádek assembleru sestavy: *error_message*|
|[Chyba kompilátoru C2760](compiler-error-c2760.md)|Chyba syntaxe: Očekává se*token1*'není*token2*.|
|[Chyba kompilátoru C2761](compiler-error-c2761.md)|'*funkce*': opětovná deklarace funkce člen není povoleno|
|[Chyba kompilátoru C2762](compiler-error-c2762.md)|'*šablony*': Neplatný výraz jako šablonu argumentu pro '*parametr*.|
|C2763 chyby kompilátoru|'*šablony*': Neplatné použití řetězcový literál jako šablonu argumentu pro '*parametr*.|
|[Chyba kompilátoru C2764](compiler-error-c2764.md)|'*parametr*': parametr šablony není používá nebo deducible v částečná specializace '*specializace*.|
|[Chyba kompilátoru C2765](compiler-error-c2765.md)|'*funkce*': explicitní specializace šablony funkce nemůže mít žádné výchozí argumenty|
|[Chyba kompilátoru C2766](compiler-error-c2766.md)|explicitní specializace; '*specializace*' již byl definován.|
|[Chyba kompilátoru C2767](compiler-error-c2767.md)|Neshoda dimenze pole spravované/WinRT: očekávaný *číslo* argumenty - *číslo* poskytuje|
|[Chyba kompilátoru C2768](compiler-error-c2768.md)|'*funkce*': Neplatné použití explicitní šablony argumenty|
|C2769 chyby kompilátoru|můžete nelze inicializovat složené závorce spravované nebo WinRT pole v seznamu inicializátoru základní nebo člen|
|[Chyba kompilátoru C2770](compiler-error-c2770.md)|Neplatný explicitní šablony nebo obecné argumenty pro '*šablony*.|
|[Chyba kompilátoru C2771](compiler-error-c2771.md)|#import povolená jenom na globální nebo oboru názvů|
|C2772 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2773](compiler-error-c2773.md)|#import a #using k dispozici pouze v kompilátoru C++|
|[Chyba kompilátoru C2774](compiler-error-c2774.md)|'*identifikátor*': žádná, put, metoda souvisí s touto vlastností|
|[Chyba kompilátoru C2775](compiler-error-c2775.md)|'*identifikátor*': žádná metoda "get" souvisí s touto vlastností|
|[Chyba kompilátoru C2776](compiler-error-c2776.md)|jeden vlastnost lze zadat pouze jednu metodu "get"|
|[Chyba kompilátoru C2777](compiler-error-c2777.md)|jeden vlastnost lze zadat pouze jednu metodu 'put.|
|[Chyba kompilátoru C2778](compiler-error-c2778.md)|nesprávně formátovaný GUID v __declspec(uuid())|
|[Chyba kompilátoru C2779](compiler-error-c2779.md)|'*deklarace*': metody vlastností může být přidružen pouze nestatické datové členy|
|[Chyba kompilátoru C2780](compiler-error-c2780.md)|'*deklarace*': očekává *číslo* argumenty - *číslo* poskytuje|
|[Chyba kompilátoru C2781](compiler-error-c2781.md)|'*deklarace*': očekává aspoň *číslo* argument - *číslo* poskytuje|
|[Chyba kompilátoru C2782](compiler-error-c2782.md)|'*deklarace*': šablony nebo obecný parametr '*parametr*' je nejednoznačný|
|[Chyba kompilátoru C2783](compiler-error-c2783.md)|'*deklarace*': nelze odvodit šablony nebo obecného argument pro '*identifikátor*.|
|[Chyba kompilátoru C2784](compiler-error-c2784.md)|'*deklarace*': nelze odvodit šablony nebo obecného argument pro '*type1*'z'*type2*.|
|[Chyba kompilátoru C2785](compiler-error-c2785.md)|'*declaration1*'a'*declaration2*se mají různé návratové typy|
|[Chyba kompilátoru C2786](compiler-error-c2786.md)|'*typ*': Neplatný operand pro __uuidof –|
|[Chyba kompilátoru C2787](compiler-error-c2787.md)|'*identifikátor*': žádný identifikátor GUID je přidružen k tomuto objektu|
|[Chyba kompilátoru C2788](compiler-error-c2788.md)|'*identifikátor*': více než jeden identifikátor GUID přidružené k tomuto objektu|
|C2789 chyby kompilátoru|'*identifikátor*': objekt const kvalifikovaný typ se musí inicializovat.|
|[Chyba kompilátoru C2790](compiler-error-c2790.md)|'super: Toto klíčové slovo lze použít pouze v hlavní funkce člena třídy|
|[Chyba kompilátoru C2791](compiler-error-c2791.md)|Neplatné použití 'super': '*třída*' nemá všechny základní třídy|
|[Chyba kompilátoru C2792](compiler-error-c2792.md)|'super: musí být následováno toto klíčové slovo '::'|
|[Chyba kompilátoru C2793](compiler-error-c2793.md)|'*tokenu*': Neočekávaný token následující '::', identifikátor nebo očekáván operátor – klíčové slovo|
|[Chyba kompilátoru C2794](compiler-error-c2794.md)|'*identifikátor*': není členem žádné přímý nebo nepřímý základní třídu '*– třída*.|
|[Chyba kompilátoru C2795](compiler-error-c2795.md)|' super::*identifikátor*' není členské funkce|
|C2796 chyby kompilátoru|ref nové lze použít pouze k vytvoření instance typu WinRT|
|[Chyba kompilátoru C2797](compiler-error-c2797.md)|(Zastaralé) '*identifikátor*': Inicializace seznamu uvnitř inicializátoru seznamu členů nebo data nestatické členské inicializátoru není implementována.|
|[Chyba kompilátoru C2798](compiler-error-c2798.md)|' super::*identifikátor*' je nejednoznačný|
|C2799 chyby kompilátoru|'*identifikátor*': je nutné inicializovat objekt const kvalifikovaný – třída typu bez zadaný uživatelem výchozí konstruktor|
