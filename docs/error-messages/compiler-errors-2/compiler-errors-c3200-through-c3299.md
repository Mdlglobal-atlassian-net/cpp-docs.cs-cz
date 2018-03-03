---
title: "C3200 chyby kompilátoru prostřednictvím C3299 | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
helpviewer_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
dev_langs:
- C++
ms.assetid: 6b3104f6-63bc-4823-b6f3-b8a16be4b87f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 339a4e0f1337e120d192515cecd4dba4e04e310e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c3200-through-c3299"></a>C3200 chyby kompilátoru prostřednictvím C3299

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C3200](compiler-error-c3200.md)|'*typ*': šablony neplatný argument pro parametr šablony,*parametr*', očekává šablonu – třída|
|[Chyba kompilátoru C3201](compiler-error-c3201.md)|Seznam parametrů šablony pro šablony třídy '*šablony*'neodpovídá seznamu parametrů šablony pro parametr šablony,*parametr*.|
|[Chyba kompilátoru C3202](compiler-error-c3202.md)|'*identifikátor*': neplatné výchozí argument, očekává šablonu – třída|
|[Chyba kompilátoru C3203](compiler-error-c3203.md)|'*identifikátor*': unspecialized třída šablony nebo obecného nelze použít jako šablonu nebo obecného argument pro parametr šablony nebo obecného '*parametr*', očekávaný skutečné typ|
|[Chyba kompilátoru C3204](compiler-error-c3204.md)|'*funkce*' nelze volat v rámci bloku catch|
|[Chyba kompilátoru C3205](compiler-error-c3205.md)|Seznam argumentů pro parametr šablony šablony '*identifikátor*' chybí|
|[Chyba kompilátoru C3206](compiler-error-c3206.md)|'*funkce*': Neplatný šablony nebo obecného argument pro '*šablony*', chybějící seznam argumentů šablony nebo obecná třída šablony/obecných '*typu*.|
|[Chyba kompilátoru C3207](compiler-error-c3207.md)|'*funkce*': argument neplatný šablony pro '*parametr*', očekává šablona třídy|
|[Chyba kompilátoru C3208](compiler-error-c3208.md)|'*funkce*': seznam parametrů šablony pro šablony třídy '*šablony*'neodpovídá seznam parametrů šablony pro parametr šablony šablony'*parametr*.|
|[Chyba kompilátoru C3209](compiler-error-c3209.md)|'*typ*': Obecná třída musí být spravované nebo WinRT třída|
|[Chyba kompilátoru C3210](compiler-error-c3210.md)|'*identifikátor*': deklarace přístup můžete použít pouze pro člena základní třídy|
|[Chyba kompilátoru C3211](compiler-error-c3211.md)|'*funkce*': explicitní specializace je pomocí syntaxe částečná specializace, použijte místo toho <> šablony|
|[Chyba kompilátoru C3212](compiler-error-c3212.md)|'*funkce*': explicitní specializace šablony člena musí být členem skupiny explicitní specializace|
|[Chyba kompilátoru C3213](compiler-error-c3213.md)|Základní třída*třída*je méně přístupný než*derived_class*.|
|[Chyba kompilátoru C3214](compiler-error-c3214.md)|'*argument*': Neplatný typ argumentu pro obecný parametr '*parametr*'z obecného'*typ*', nesplňuje omezení '*omezení*'|
|[Chyba kompilátoru C3215](compiler-error-c3215.md)|'*constraint1*': Parametr obecného typu již omezené '*constraint2*.|
|[Chyba kompilátoru C3216](compiler-error-c3216.md)|omezení nesmí být obecný parametr '*typu*.|
|[Chyba kompilátoru C3217](compiler-error-c3217.md)|'*parametr*': obecný parametr nemůže být omezen v této deklarace|
|[Chyba kompilátoru C3218](compiler-error-c3218.md)|'*typ*': není povolena jako omezení typu|
|[Chyba kompilátoru C3219](compiler-error-c3219.md)|'*parametr*': obecný parametr nemůže být omezené více bez – rozhraní: '*typu*.|
|C3220 chyby kompilátoru|'*rozhraní*': rozhraní nemůže mít progid|
|C3221 chyby kompilátoru|'*člen*': více "default" a 'případu' atributy nejsou povoleny na člena|
|[Chyba kompilátoru C3222](compiler-error-c3222.md)|'*funkce*': výchozí argumenty pro člena nelze deklarovat, funkce spravované nebo WinRT typu nebo obecné funkce|
|[Chyba kompilátoru C3223](compiler-error-c3223.md)|'*vlastnost*': 'typeid' nelze použít pro vlastnost|
|[Chyba kompilátoru C3224](compiler-error-c3224.md)|'*typ*': žádné přetížené obecná třída trvá*číslo*' argumenty obecného typu|
|[Chyba kompilátoru C3225](compiler-error-c3225.md)|argument obecného typu '*argument*'nemůže být'*typ*', musí být typu hodnoty nebo popisovač pro typu odkazu.|
|[Chyba kompilátoru C3226](compiler-error-c3226.md)|Deklaraci šablony není povolený v deklaraci obecné|
|[Chyba kompilátoru C3227](compiler-error-c3227.md)|'*typ*': nelze použít se*operátor*' přidělit obecného typu|
|[Chyba kompilátoru C3228](compiler-error-c3228.md)|'*funkce*': argument obecného typu '*argument*'nemůže být'*typ*', musí to být hodnota typu nebo zpracovat typ|
|[Chyba kompilátoru C3229](compiler-error-c3229.md)|'*typ*': indirections na parametr obecného typu nejsou povoleny.|
|[Chyba kompilátoru C3230](compiler-error-c3230.md)|'*funkce*': argument typu šablony pro '*argument*' nemůže obsahovat parametr obecného typu: '*typu*.|
|[Chyba kompilátoru C3231](compiler-error-c3231.md)|'*typ*': argument typu šablonu nelze použít parametr obecného typu|
|[Chyba kompilátoru C3232](compiler-error-c3232.md)|'*parametr*': Parametr obecného typu nelze použít kvalifikovaný název|
|[Chyba kompilátoru C3233](compiler-error-c3233.md)|'*typ*': Parametr obecného typu již omezené.|
|[Chyba kompilátoru C3234](compiler-error-c3234.md)|Obecné třídy se nesmí odvozovat od parametr obecného typu|
|[Chyba kompilátoru C3235](compiler-error-c3235.md)|'*specializace*': explicitní nebo jeho část specializace obecné třídy není povoleno.|
|[Chyba kompilátoru C3236](compiler-error-c3236.md)|Explicitní vytvoření instance služby obecný není povolen.|
|[Chyba kompilátoru C3237](compiler-error-c3237.md)|'*třída*': Obecné třídy nemůže být vlastní atribut|
|[Chyba kompilátoru C3238](compiler-error-c3238.md)|'*typ*': typ s tímto názvem již byla předána do sestavení '*sestavení*.|
|[Chyba kompilátoru C3239](compiler-error-c3239.md)|'*typ*': ukazatel na ukazatel interior nebo kódu pin je zakázán modul common language runtime|
|[Chyba kompilátoru C3240](compiler-error-c3240.md)|'*identifikátor*': musí být-přetížený abstraktní členské funkce '*typu*.|
|[Chyba kompilátoru C3241](compiler-error-c3241.md)|'*člen*': Tato metoda nebyla zaváděné '*rozhraní*.|
|[Chyba kompilátoru C3242](compiler-error-c3242.md)|'*funkce*': pouze explicitně můžete přepsat virtuální funkce|
|[Chyba kompilátoru C3243](compiler-error-c3243.md)|Žádné přetížení funkce byly zavedeny '*rozhraní*.|
|[Chyba kompilátoru C3244](compiler-error-c3244.md)|'*člen*': Tato metoda byla zavedena ve '*interface1*, ne podle'*interface2*.|
|C3245 chyby kompilátoru|'*funkce*': použití proměnných šablony vyžaduje argument seznam šablon|
|[Chyba kompilátoru C3246](compiler-error-c3246.md)|'*– třída*': nemůže Zdědit z '*base_class*, protože byla deklarována jako'*dědičnosti*.|
|[Chyba kompilátoru C3247](compiler-error-c3247.md)|'*třída typu coclass*': coclass nemůže Zdědit z jiné coclass*base_class*.|
|[Chyba kompilátoru C3248](compiler-error-c3248.md)|Zastaralé. '*funkce*': funkce deklarována jako 'zapečetěné' nelze přepsat,*funkce*.|
|C3249 chyby kompilátoru|Neplatný příkaz nebo dílčí výrazu pro funkci "constexpr.|
|C3250 chyby kompilátoru|'*deklarace*': deklarace není povolen v tělo funkce 'constexpr.|
|[Chyba kompilátoru C3251](compiler-error-c3251.md)|nejde volat metodu základní třídy na typ instance hodnota|
|[Chyba kompilátoru C3252](compiler-error-c3252.md)|'*funkce*': usnadnění virtuální metody v typu spravované nebo WinRT nelze zmenšit.|
|[Chyba kompilátoru C3253](compiler-error-c3253.md)|'*funkce*": chyby s explicitní přepsání|
|[Chyba kompilátoru C3254](compiler-error-c3254.md)|'*funkce*': třída obsahuje explicitní přepsání '*funkce*', ale není odvozen z rozhraní, které obsahuje deklarace funkce|
|[Chyba kompilátoru C3255](compiler-error-c3255.md)|'*typ*': nelze dynamicky přidělit objekt typu tuto hodnotu na nativní haldy|
|C3256 chyby kompilátoru|'*funkce*': proměnné použití nevytváří konstantní výraz|
|C3257 chyby kompilátoru|Zastaralé.|
|C3258 chyby kompilátoru|Zastaralé.|
|C3259 chyby kompilátoru|Funkce 'constexpr' může mít pouze jeden příkaz return|
|C3260 chyby kompilátoru|'*tokenu*': Přeskočení neočekávané tokeny před lambda textu|
|C3261 chyby kompilátoru|funkce vrácení spravované nebo WinRT pole musí mít závorky pole na konci deklaraci: '*identifikátor*(...) []'|
|[Chyba kompilátoru C3262](compiler-error-c3262.md)|Neplatné pole indexování: *číslo* dimenze (dimenzí) zadaný pro *číslo*-dimenzí '*typu*.|
|C3263 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3264](compiler-error-c3264.md)|'*identifikátor*': Třída – konstruktor nemůže mít typ vrácené hodnoty.|
|[Chyba kompilátoru C3265](compiler-error-c3265.md)|nelze deklarovat spravované '*managed_construct*"v nespravované'*unmanaged_construct*.|
|[Chyba kompilátoru C3266](compiler-error-c3266.md)|'*funkce*': konstruktoru třídy musí mít seznam parametrů, void.|
|C3267 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3268](compiler-error-c3268.md)|'*funkce*': Obecné funkce nebo členské funkce obecné třídy nemůže mít seznam proměnných parametrů|
|[Chyba kompilátoru C3269](compiler-error-c3269.md)|'*funkce*': členské – funkce typu spravované nebo WinRT nelze deklarovat s '...|
|[Chyba kompilátoru C3270](compiler-error-c3270.md)|'*pole*': atribut FieldOffset lze použít pouze v kontextu StructLayout(LayoutKind::Explicit)|
|[Chyba kompilátoru C3271](compiler-error-c3271.md)|'*pole*': Neplatná hodnota '*číslo*' pro atribut FieldOffset|
|[Chyba kompilátoru C3272](compiler-error-c3272.md)|'*symbol*': symbol vyžaduje FieldOffset, jako je členem struktura nebo třídy *type_name* definovaný s StructLayout(LayoutKind::Explicit)|
|[Chyba kompilátoru C3273](compiler-error-c3273.md)|'*– klíčové slovo*': není povoleno v bloku try C++|
|[Chyba kompilátoru C3274](compiler-error-c3274.md)|Nakonec / &#95; &#95; nakonec bez odpovídající akci|
|[Chyba kompilátoru C3275](compiler-error-c3275.md)|'*identifikátor*': nemůžete použít tento symbol bez kvalifikátoru|
|[Chyba kompilátoru C3276](compiler-error-c3276.md)|'*– klíčové slovo*': přejít z nakonec / &#95; &#95; nakonec má bloku undefined chování při ukončení zpracování|
|[Chyba kompilátoru C3277](compiler-error-c3277.md)|nelze definovat nespravované výčet '*– výčet*uvnitř spravované*typu*.|
|[Chyba kompilátoru C3278](compiler-error-c3278.md)|přímé volání rozhraní nebo čisté metoda '*funkce*, se nezdaří za běhu|
|[Chyba kompilátoru C3279](compiler-error-c3279.md)|částečné a explicitní specializací také jako explicitní instancí možnosti šablony třídy deklarované v oboru názvů rozhraní příkazového řádku nejsou povoleny.|
|[Chyba kompilátoru C3280](compiler-error-c3280.md)|'*funkce*': členské funkce spravovaného typu nelze kompilovat, jako nespravované funkce|
|C3281 chyby kompilátoru|'*funkce*': globální operátor nemůže mít typ spravované/WinRT '*typ*' v podpisu|
|[Chyba kompilátoru C3282](compiler-error-c3282.md)|obecný parametr seznamy se může vyskytovat pouze na spravované nebo WinRT třídy, struktury nebo funkce|
|[Chyba kompilátoru C3283](compiler-error-c3283.md)|'*rozhraní*': rozhraní nemůže mít konstruktoru instance|
|[Chyba kompilátoru C3284](compiler-error-c3284.md)|omezení pro obecný parametr '*parametr*"funkce"*deklarátor*'omezení pro obecný parametr musí shodovat.'*parametr*"funkce"*deklarátor*.|
|[Chyba kompilátoru C3285](compiler-error-c3285.md)|pro každý příkaz nemůže pracovat s proměnnými typu '*typu*.|
|[Chyba kompilátoru C3286](compiler-error-c3286.md)|'*specifikátor*': Proměnná iterace nemůže mít žádné specifikátory třídy úložiště|
|[Chyba kompilátoru C3287](compiler-error-c3287.md)|Typ '*typ*' (návratový typ GetEnumerator) musí mít aktuální veřejné vlastnosti a vhodný veřejné MoveNext – členská funkce|
|[Chyba kompilátoru C3288](compiler-error-c3288.md)|'*typ*': Neplatná dereference popisovač typu|
|[Chyba kompilátoru C3289](compiler-error-c3289.md)|'*identifikátor*': trivial vlastnost není možné indexovat.|
|[Chyba kompilátoru C3290](compiler-error-c3290.md)|'*typ*': trivial vlastnost nemůže mít typ odkazu|
|[Chyba kompilátoru C3291](compiler-error-c3291.md)|"default": nemůže být název trivial vlastnosti|
|[Chyba kompilátoru C3292](compiler-error-c3292.md)|nelze znovu otevřít obor názvů rozhraní příkazového řádku|
|[Chyba kompilátoru C3293](compiler-error-c3293.md)|'*identifikátor*":"default"používat pro přístup k výchozí vlastnost (indexer) pro třídu*– třída*.|
|C3294 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3295](compiler-error-c3295.md)|' #pragma *specifikátor*se dá použít jenom na globální nebo oboru názvů|
|[Chyba kompilátoru C3296](compiler-error-c3296.md)|'*identifikátor*': vlastnost s tímto názvem již existuje.|
|[Chyba kompilátoru C3297](compiler-error-c3297.md)|' *constraint2*': nelze použít se *constraint1*' jako omezení protože ' *constraint1*' má hodnotu omezení|
|[Chyba kompilátoru C3298](compiler-error-c3298.md)|' *constraint1*': nelze použít se *constraint2*' jako omezení protože ' *constraint2*' obsahuje omezení ref a ' *constraint1*. má hodnotu omezení|
|[Chyba kompilátoru C3299](compiler-error-c3299.md)|' *funkce*': nelze zadat omezení, se dědí z základní metody|
