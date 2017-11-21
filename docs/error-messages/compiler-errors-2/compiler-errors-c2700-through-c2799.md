---
title: "C2700 chyby kompilátoru prostřednictvím C2799 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8246cec8db138b053f3c239448043147131166c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2700-through-c2799"></a>C2700 chyby kompilátoru prostřednictvím C2799
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|[C2700 chyby kompilátoru](compiler-error-c2700.md)|'*typ*': nemůže být vyvolána (/W4 použijte další informace)|  
|[C2701 chyby kompilátoru](compiler-error-c2701.md)|'*funkce*': funkce šablony nebo obecný nemůže být friend místní třídy|  
|[C2702 chyby kompilátoru](compiler-error-c2702.md)| __except se nemůže nacházet v bloku ukončení|  
|[C2703 chyby kompilátoru](compiler-error-c2703.md)|Neplatný __leave – příkaz|  
|[C2704 chyby kompilátoru](compiler-error-c2704.md)|'*funkce*': __va_start vnitřní povoleny pouze v vararg|  
|[C2705 chyby kompilátoru](compiler-error-c2705.md)|'*popisek*': Neplatný přechod do "*exception_block*' oboru|  
|[C2706 chyby kompilátoru](compiler-error-c2706.md)|Neplatný __except bez odpovídající __try (chybějící '}' v blok __try?)|  
|[C2707 chyby kompilátoru](compiler-error-c2707.md)|'*identifikátor*': Chybný kontext pro vnitřní funkce|  
|[C2708 chyby kompilátoru](compiler-error-c2708.md)|'*identifikátor*': parametry skutečná délka v bajtech se liší od předchozího volání nebo odkaz|  
|[C2709 chyby kompilátoru](compiler-error-c2709.md)|'*identifikátor*': formální parametry Délka v bajtech se liší od předchozí deklarace|  
|[C2710 chyby kompilátoru](compiler-error-c2710.md)|'*identifikátor*': ' __declspec (*modifikátor*), lze použít pouze na funkci vrácení ukazatele|  
|[C2711 chyby kompilátoru](compiler-error-c2711.md)|'*funkce*': tuto funkci nelze zkompilovat jako spravovaný, zvažte použití #pragma nespravované|  
|[C2712 chyby kompilátoru](compiler-error-c2712.md)|nelze použít __try ve funkcích, které vyžadují unwinding objektu|  
|[C2713 chyby kompilátoru](compiler-error-c2713.md)|pouze jednu formu povolený na základě funkce zpracování výjimek|  
|[C2714 chyby kompilátoru](compiler-error-c2714.md)|alignof(void) není povolen.|  
|[C2715 chyby kompilátoru](compiler-error-c2715.md)|'*typ*': nelze vyvolat nebo catch tento typ|  
|C2716 chyby kompilátoru|Zastaralé.|  
|C2717 chyby kompilátoru|Zastaralé.|  
|[C2718 chyby kompilátoru](compiler-error-c2718.md)|'*typ*': skutečný parametr s požadovanou zarovnání *číslo* nebude zarovnán|  
|[C2719 chyby kompilátoru](compiler-error-c2719.md)|'*parametr*': formální parametr s požadovanou zarovnání *číslo* nebude zarovnán|  
|[C2720 chyby kompilátoru](compiler-error-c2720.md)|'*identifikátor*': '*specifikátor*' u členů Neplatný specifikátor třídy úložiště|  
|[C2721 chyby kompilátoru](compiler-error-c2721.md)|'*specifikátor*': Neplatný mezi – klíčové slovo operátoru a typ specifikátor třídy úložiště|  
|[C2722 chyby kompilátoru](compiler-error-c2722.md)|'::*operátor*': neplatný příkaz následující operátor; použijte ' operátor *operátor*.|  
|[C2723 chyby kompilátoru](compiler-error-c2723.md)|'*funkce*': '*specifikátor*' v definici funkce Neplatný specifikátor|  
|[C2724 chyby kompilátoru](compiler-error-c2724.md)|'*funkce*":"statická"by se neměla používat na členské funkce, které jsou definované v souboru oboru|  
|[C2725 chyby kompilátoru](compiler-error-c2725.md)|'*typ*': nelze vyvolat nebo catch objekt spravované nebo WinRT hodnotou nebo odkazem|  
|[C2726 chyby kompilátoru](compiler-error-c2726.md)|'gcnew, může použít pouze pro vytvoření objektu s typem spravované nebo WinRT|  
|C2727 chyby kompilátoru|Zastaralé.|  
|[C2728 chyby kompilátoru](compiler-error-c2728.md)|'*typ*': nativní pole nemůže obsahovat tento typ|  
|C2729 chyby kompilátoru|Zastaralé.|  
|[C2730 chyby kompilátoru](compiler-error-c2730.md)|'*třída*': nemůže být základní třídu sám sebe|  
|[C2731 chyby kompilátoru](compiler-error-c2731.md)|'*funkce*': funkce nemohou být přetíženy.|  
|[C2732 chyby kompilátoru](compiler-error-c2732.md)|starší specifikace pro specifikaci propojení v rozporu se*funkce*.|  
|[C2733 chyby kompilátoru](compiler-error-c2733.md)|'*funkce*': druhé C propojení přetížené funkce není povoleno|  
|[C2734 chyby kompilátoru](compiler-error-c2734.md)|'*identifikátor*': 'const' objekt musí inicializovat, pokud není extern|  
|[C2735 chyby kompilátoru](compiler-error-c2735.md)|'*– klíčové slovo*' není v specifikátor typu formální parametr povoleno – klíčové slovo|  
|[C2736 chyby kompilátoru](compiler-error-c2736.md)|'*– klíčové slovo*' – klíčové slovo není povolena v přetypování|  
|C2737 chyby kompilátoru|'*identifikátor*': 'constexpr' objekt musí být inicializován.|  
|[C2738 chyby kompilátoru](compiler-error-c2738.md)|' operátor *typ*': je nejednoznačné, nebo není členem '*– třída*.|  
|[C2739 chyby kompilátoru](compiler-error-c2739.md)|'*číslo*': explicitní pole spravované nebo WinRT dimenze musí být mezi 1 a 32.|  
|C2740 chyby kompilátoru|Hodnota operand '*číslo*"je mimo rozsah"*lower_bound –* - *upper_bound –*.|  
|C2741 chyby kompilátoru|rámce příliš velký.|  
|C2742 chyby kompilátoru|Zastaralé.|  
|[C2743 chyby kompilátoru](compiler-error-c2743.md)|'*typ*': nelze catch nativního typu s __clrcall – destruktor nebo kopírovací konstruktor|  
|C2744 chyby kompilátoru|'*operátor*' není platný operátor CLR nebo WinRT|  
|[C2745 chyby kompilátoru](compiler-error-c2745.md)|'*tokenu*': Tento token nelze převést na identifikátor|  
|C2746 chyby kompilátoru|Zastaralé.|  
|C2747 chyby kompilátoru|Zastaralé.|  
|[C2748 chyby kompilátoru](compiler-error-c2748.md)|Vytvoření spravované nebo WinRT pole musí mít velikost pole nebo pole inicializátoru|  
|[C2749 chyby kompilátoru](compiler-error-c2749.md)|'*typ*': můžete pouze throw a catch popisovač pro spravované třídy s/clr: safe|  
|[C2750 chyby kompilátoru](compiler-error-c2750.md)|'*typ*': nelze použít nové na odkaz na typ; místo toho použijte 'gcnew.|  
|[C2751 chyby kompilátoru](compiler-error-c2751.md)|'*parametr*': nemůže být kvalifikovaný název parametru – funkce|  
|[C2752 chyby kompilátoru](compiler-error-c2752.md)|'*šablony*': odpovídá více než jeden částečná specializace šablony seznam argumentů|  
|[C2753 chyby kompilátoru](compiler-error-c2753.md)|'*šablony*': částečná specializace se nemůže shodovat seznam argumentů pro primární šablony|  
|[C2754 chyby kompilátoru](compiler-error-c2754.md)|'*šablony*': částečná specializace nemůže mít parametr závislé bez typu šablony|  
|[C2755 chyby kompilátoru](compiler-error-c2755.md)|'*parametr*': parametr není typu částečná specializace musí být jednoduchý identifikátor|  
|[C2756 chyby kompilátoru](compiler-error-c2756.md)|'*šablony*': výchozí šablony argumenty nejsou povoleny na částečná specializace|  
|[C2757 chyby kompilátoru](compiler-error-c2757.md)|'*identifikátor*': symbol s tímto názvem již existuje, a proto nelze tento název použít jako název oboru názvů|  
|[C2758 chyby kompilátoru](compiler-error-c2758.md)|'*člen*': členem typ odkazu musí být inicializován.|  
|C2759 chyby kompilátoru|řádek assembleru sestavy: *error_message*|  
|[C2760 chyby kompilátoru](compiler-error-c2760.md)|Chyba syntaxe: Očekává se*token1*'není*token2*.|  
|[C2761 chyby kompilátoru](compiler-error-c2761.md)|'*funkce*': opětovná deklarace funkce člen není povoleno|  
|[C2762 chyby kompilátoru](compiler-error-c2762.md)|'*šablony*': Neplatný výraz jako šablonu argumentu pro '*parametr*.|  
|C2763 chyby kompilátoru|'*šablony*': Neplatné použití řetězcový literál jako šablonu argumentu pro '*parametr*.|  
|[C2764 chyby kompilátoru](compiler-error-c2764.md)|'*parametr*': parametr šablony není používá nebo deducible v částečná specializace '*specializace*.|  
|[C2765 chyby kompilátoru](compiler-error-c2765.md)|'*funkce*': explicitní specializace šablony funkce nemůže mít žádné výchozí argumenty|  
|[C2766 chyby kompilátoru](compiler-error-c2766.md)|explicitní specializace; '*specializace*' již byl definován.|  
|[C2767 chyby kompilátoru](compiler-error-c2767.md)|Neshoda dimenze pole spravované/WinRT: očekávaný *číslo* argumenty - *číslo* poskytuje|  
|[C2768 chyby kompilátoru](compiler-error-c2768.md)|'*funkce*': Neplatné použití explicitní šablony argumenty|  
|C2769 chyby kompilátoru|můžete nelze inicializovat složené závorce spravované nebo WinRT pole v seznamu inicializátoru základní nebo člen|  
|[C2770 chyby kompilátoru](compiler-error-c2770.md)|Neplatný explicitní šablony nebo obecné argumenty pro '*šablony*.|  
|[C2771 chyby kompilátoru](compiler-error-c2771.md)|#import povolená jenom na globální nebo oboru názvů|  
|C2772 chyby kompilátoru|Zastaralé.|  
|[C2773 chyby kompilátoru](compiler-error-c2773.md)|#import a #using k dispozici pouze v kompilátoru C++|  
|[C2774 chyby kompilátoru](compiler-error-c2774.md)|'*identifikátor*': žádná, put, metoda souvisí s touto vlastností|  
|[C2775 chyby kompilátoru](compiler-error-c2775.md)|'*identifikátor*': žádná metoda "get" souvisí s touto vlastností|  
|[C2776 chyby kompilátoru](compiler-error-c2776.md)|jeden vlastnost lze zadat pouze jednu metodu "get"|  
|[C2777 chyby kompilátoru](compiler-error-c2777.md)|jeden vlastnost lze zadat pouze jednu metodu 'put.|  
|[C2778 chyby kompilátoru](compiler-error-c2778.md)|nesprávně formátovaný GUID v __declspec(uuid())|  
|[C2779 chyby kompilátoru](compiler-error-c2779.md)|'*deklarace*': metody vlastností může být přidružen pouze nestatické datové členy|  
|[C2780 chyby kompilátoru](compiler-error-c2780.md)|'*deklarace*': očekává *číslo* argumenty - *číslo* poskytuje|  
|[C2781 chyby kompilátoru](compiler-error-c2781.md)|'*deklarace*': očekává aspoň *číslo* argument - *číslo* poskytuje|  
|[C2782 chyby kompilátoru](compiler-error-c2782.md)|'*deklarace*': šablony nebo obecný parametr '*parametr*' je nejednoznačný|  
|[C2783 chyby kompilátoru](compiler-error-c2783.md)|'*deklarace*': nelze odvodit šablony nebo obecného argument pro '*identifikátor*.|  
|[C2784 chyby kompilátoru](compiler-error-c2784.md)|'*deklarace*': nelze odvodit šablony nebo obecného argument pro '*type1*'z'*type2*.|  
|[C2785 chyby kompilátoru](compiler-error-c2785.md)|'*declaration1*'a'*declaration2*se mají různé návratové typy|  
|[C2786 chyby kompilátoru](compiler-error-c2786.md)|'*typ*': Neplatný operand pro __uuidof –|  
|[C2787 chyby kompilátoru](compiler-error-c2787.md)|'*identifikátor*': žádný identifikátor GUID je přidružen k tomuto objektu|  
|[C2788 chyby kompilátoru](compiler-error-c2788.md)|'*identifikátor*': více než jeden identifikátor GUID přidružené k tomuto objektu|  
|C2789 chyby kompilátoru|'*identifikátor*': objekt const kvalifikovaný typ se musí inicializovat.|  
|[C2790 chyby kompilátoru](compiler-error-c2790.md)|'super: Toto klíčové slovo lze použít pouze v hlavní funkce člena třídy|  
|[C2791 chyby kompilátoru](compiler-error-c2791.md)|Neplatné použití 'super': '*třída*' nemá všechny základní třídy|  
|[C2792 chyby kompilátoru](compiler-error-c2792.md)|'super: musí být následováno toto klíčové slovo '::'|  
|[C2793 chyby kompilátoru](compiler-error-c2793.md)|'*tokenu*': Neočekávaný token následující '::', identifikátor nebo očekáván operátor – klíčové slovo|  
|[C2794 chyby kompilátoru](compiler-error-c2794.md)|'*identifikátor*': není členem žádné přímý nebo nepřímý základní třídu '*– třída*.|  
|[C2795 chyby kompilátoru](compiler-error-c2795.md)|' super::*identifikátor*' není členské funkce|  
|C2796 chyby kompilátoru|ref nové lze použít pouze k vytvoření instance typu WinRT|  
|[Chyba kompilátoru C2797](compiler-error-c2797.md)|(Zastaralé) '*identifikátor*': Inicializace seznamu uvnitř inicializátoru seznamu členů nebo data nestatické členské inicializátoru není implementována.|  
|[C2798 chyby kompilátoru](compiler-error-c2798.md)|' super::*identifikátor*' je nejednoznačný|  
|C2799 chyby kompilátoru|'*identifikátor*': je nutné inicializovat objekt const kvalifikovaný – třída typu bez zadaný uživatelem výchozí konstruktor|  
