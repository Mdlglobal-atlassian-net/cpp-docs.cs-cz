---
title: C3100 chyby kompilátoru prostřednictvím C3199 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
dev_langs:
- C++
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 062ab968a51c38e9418a96b0df07eec3ae399ac3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283891"
---
# <a name="compiler-errors-c3100-through-c3199"></a>C3100 chyby kompilátoru prostřednictvím C3199

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C3100](compiler-error-c3100.md)|'*identifikátor*': Neznámý atribut kvalifikátor|
|[Chyba kompilátoru C3101](compiler-error-c3101.md)|Neplatný výraz argumentu '*identifikátor*.|
|C3102 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3103](compiler-error-c3103.md)|'*identifikátor*': opakuje pojmenovaný argument|
|[Chyba kompilátoru C3104](compiler-error-c3104.md)|argument neplatný atribut|
|C3105 chyby kompilátoru|'*symbol*': nelze použít jako atribut|
|[Chyba kompilátoru C3106](compiler-error-c3106.md)|'*atribut*': nepojmenované argumenty musí předcházet pojmenované argumenty|
|C3107 chyby kompilátoru|'*atribut*': členské funkce nativní atributů nemůže být definovaný.|
|C3108 chyby kompilátoru|Typ nelze odvodit, protože inicializačním seznam není výrazu|
|C3109 chyby kompilátoru|'*identifikátor*': metody rozhraní, musíte použít buď '__stdcall' nebo '__cdecl konvence volání|
|[Chyba kompilátoru C3110](compiler-error-c3110.md)|'*funkce*': nelze přetížení metody rozhraní COM|
|C3111 chyby kompilátoru|Inicializačním seznam nelze použít jako výchozí argument pro parametr šablony|
|C3112 chyby kompilátoru|'*rozhraní*': rozhraní lze deklarovat pouze na globální nebo oboru názvů|
|[Chyba kompilátoru C3113](compiler-error-c3113.md)|'rozhraní/enum, nemůže být šablony nebo obecný|
|[Chyba kompilátoru C3114](compiler-error-c3114.md)|'*identifikátor*': není platný argument atributu s názvem|
|[Chyba kompilátoru C3115](compiler-error-c3115.md)|'*atribut*': tohoto atributu není povolená na '*vytvořit*.|
|[Chyba kompilátoru C3116](compiler-error-c3116.md)|'*specifikátor*': Třída neplatný úložiště pro rozhraní – metoda|
|[Chyba kompilátoru C3117](compiler-error-c3117.md)|'*rozhraní*': rozhraní může mít pouze jeden základní třída|
|[Chyba kompilátoru C3118](compiler-error-c3118.md)|'*rozhraní*': rozhraní nepodporují virtuální dědičnost|
|C3119 chyby kompilátoru|alignas(void) není povolen.|
|[Chyba kompilátoru C3120](compiler-error-c3120.md)|'*identifikátor*': metody rozhraní nelze práce se seznamem argumentů proměnných|
|[Chyba kompilátoru C3121](compiler-error-c3121.md)|nelze změnit identifikátor GUID pro třídu*třída*.|
|C3122 chyby kompilátoru|'*rozhraní*': Obecné rozhraní WinRT nemůže mít identifikátor GUID|
|C3123 chyby kompilátoru|Obecné rozhraní WinRT nemůže mít omezení|
|C3124 chyby kompilátoru|'podepsané char' není platný typ dat WinRT. Místo toho použijte 'unsigned char', 'wchar_t' nebo 'podepsaný krátké'.|
|C3125 chyby kompilátoru|'*typ*': typ nelze přímo nebo nepřímo odvozen od 'Platform::Exception.|
|[Chyba kompilátoru C3126](compiler-error-c3126.md)|nelze definovat sjednocení '*sjednocení*'uvnitř typu spravované/WinRT'*typu*.|
|C3127 chyby kompilátoru|'*typ*': '*znak*' znak lze použít pouze na třídě ref WinRT|
|C3128 chyby kompilátoru|'*typ*'nemá virtuální tabulku, která byla zavedena ve'*typu*.|
|C3129 chyby kompilátoru|'*typ*': __default_vptr_for_base lze použít pouze pro místně definované polymorfní typy a základů|
|[Chyba kompilátoru C3130](compiler-error-c3130.md)|Vnitřní chyba kompilátoru: se nepodařilo zapsat blok vloženého kódu do souboru PDB|
|[Chyba kompilátoru C3131](compiler-error-c3131.md)|Projekt musí mít atribut 'module' s vlastností 'name.|
|[Chyba kompilátoru C3132](compiler-error-c3132.md)|'*parametr*': pole parametrů lze použít pouze k formální argument typu 'jednorozměrná pole spravované nebo WinRT.|
|[Chyba kompilátoru C3133](compiler-error-c3133.md)|Atributy nelze použít jako vararg C++|
|[Chyba kompilátoru C3134](compiler-error-c3134.md)|'*hodnotu*': hodnota argumentu atribut '*argument*'nemá platný typ'*typu*.|
|[Chyba kompilátoru C3135](compiler-error-c3135.md)|'*identifikátor*': vlastnost nemůže mít 'const' nebo 'volatile, zadejte|
|[Chyba kompilátoru C3136](compiler-error-c3136.md)|'*rozhraní*': rozhraní modelu COM může dědit vlastnosti pouze z jiné rozhraní modelu COM,*rozhraní*' není rozhraní modelu COM|
|[Chyba kompilátoru C3137](compiler-error-c3137.md)|'*identifikátor*': vlastnost nelze inicializovat.|
|[Chyba kompilátoru C3138](compiler-error-c3138.md)|'*identifikátor*': '*atribut*' rozhraní musí dědit z IDispatch nebo z rozhraní, které dědí z IDispatch|
|[Chyba kompilátoru C3139](compiler-error-c3139.md)|'*typ*': nelze exportovat UDT bez členů|
|[Chyba kompilátoru C3140](compiler-error-c3140.md)|nemůže mít více atributů 'module' ve stejné jednotce kompilace|
|[Chyba kompilátoru C3141](compiler-error-c3141.md)|'*rozhraní*': rozhraní podporují pouze veřejné dědičnosti|
|[Chyba kompilátoru C3142](compiler-error-c3142.md)|'*vlastnost*': Nelze převzít adresu vlastnosti|
|C3143 chyby kompilátoru|'*argument*': argument atribut nemůže mít více hodnot|
|C3144 chyby kompilátoru|'*atribut*': atribut vyžaduje, aby explicitní argumenty '*argument*' nepojmenované|
|[Chyba kompilátoru C3145](compiler-error-c3145.md)|'*identifikátor*': globální nebo statické proměnné nemůže být typu spravované/WinRT '*typu*.|
|C3146 chyby kompilátoru|Zastaralé.|
|C3147 chyby kompilátoru|Zastaralé.|
|C3148 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3149](compiler-error-c3149.md)|'*typ*': nemůžete použít tento typ zde bez nejvyšší úrovně "*tokenu*.|
|[Chyba kompilátoru C3150](compiler-error-c3150.md)|'*vytvořit*': '*atribut*' lze použít pouze k třída, struktura, rozhraní, pole nebo ukazatele|
|C3151 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3152](compiler-error-c3152.md)|'*funkce*': '*– klíčové slovo*' lze použít pouze k třída, struktura nebo člena virtuální funkce|
|[Chyba kompilátoru C3153](compiler-error-c3153.md)|'*rozhraní*': Nelze vytvořit instanci rozhraní|
|[Chyba kompilátoru C3154](compiler-error-c3154.md)|Očekávaný ',' než třemi tečkami. Non-oddělených třemi tečkami na parametr pole funkce není podporován.|
|[Chyba kompilátoru C3155](compiler-error-c3155.md)|atributy nejsou povoleny v vlastnost indexeru|
|[Chyba kompilátoru C3156](compiler-error-c3156.md)|'*třída*': nemůže mít místní definice typu spravované nebo WinRT|
|[Chyba kompilátoru C3157](compiler-error-c3157.md)|ParamArray atribut lze použít pouze na poslední parametr|
|C3158 chyby kompilátoru|'*funkce*': '*– klíčové slovo*' lze použít pouze pro virtuální členské funkce|
|[Chyba kompilátoru C3159](compiler-error-c3159.md)|'*identifikátor*': nelze deklarovat pole ukazatelé na typ hodnoty|
|[Chyba kompilátoru C3160](compiler-error-c3160.md)|'*typ*': datový člen třídy spravované nebo WinRT nemůže mít tento typ|
|[Chyba kompilátoru C3161](compiler-error-c3161.md)|'*rozhraní*': vnoření třída, struktura nebo rozhraní v rozhraní je neplatný; vnoření rozhraní ve třídě nebo struktuře je neplatný|
|[Chyba kompilátoru C3162](compiler-error-c3162.md)|'*typ*': odkaz na typ, který má destruktor nelze použít jako typ člena statických dat '*člen*.|
|[Chyba kompilátoru C3163](compiler-error-c3163.md)|'*třída*': atributy, které jsou konzistentní s předchozí deklarace|
|C3164 chyby kompilátoru|Zastaralé.|
|C3165 chyby kompilátoru|'*hodnotu*': nelze převést na hodnotu integrální nebo plovoucí bodu|
|[Chyba kompilátoru C3166](compiler-error-c3166.md)|Zastaralé. '*typ*': datový člen třídy spravované nebo WinRT nemůže mít typ '*pointer_type* na vnitřních *managed_pointer_type*.|
|[Chyba kompilátoru C3167](compiler-error-c3167.md)|Nelze inicializovat rozhraní .NET Framework: Zajistěte, aby je nainstalovaná|
|[Chyba kompilátoru C3168](compiler-error-c3168.md)|'*typ*': Neplatná základní typ pro příkaz enum|
|C3169 chyby kompilátoru|'*typ*': nelze odvodit typ 'auto' z '*typu*.|
|[Chyba kompilátoru C3170](compiler-error-c3170.md)|nemůže mít jiného modulu identifikátory v projektu|
|[Chyba kompilátoru C3171](compiler-error-c3171.md)|'*modulu*': nelze zadat jiný modul atributy v projektu|
|[Chyba kompilátoru C3172](compiler-error-c3172.md)|'*identifikátor*': v projektu nelze zadat jiný idl_module – atributy|
|[Chyba kompilátoru C3173](compiler-error-c3173.md)|zjistila se Neshoda verzí v idl sloučení|
|[Chyba kompilátoru C3174](compiler-error-c3174.md)|nebyl zadán atribut modulu|
|[Chyba kompilátoru C3175](compiler-error-c3175.md)|'*funkce*': nelze volat metodu spravovaného typu z nespravovaných funkce '*funkce*.|
|[Chyba kompilátoru C3176](compiler-error-c3176.md)|'*typ*': nelze deklarovat typ místní hodnoty|
|C3177 chyby kompilátoru|nemůže mít funkci pro převod na typ, který obsahuje '*typu*.|
|C3178 chyby kompilátoru|'*typ*': ParamArray nelze použít ve funkci s výchozí argumenty|
|[Chyba kompilátoru C3179](compiler-error-c3179.md)|Typ nepojmenované spravované nebo WinRT není povolena.|
|[Chyba kompilátoru C3180](compiler-error-c3180.md)|'*typ*': název překračuje limit meta-data "*číslo*' znaků|
|[Chyba kompilátoru C3181](compiler-error-c3181.md)|'*typ*': Neplatný operand pro *– operátor*|
|[Chyba kompilátoru C3182](compiler-error-c3182.md)|'*typ*': Deklarace členů pomocí deklarace nebo přístup není povolen v rámci spravované nebo WinRT typu|
|[Chyba kompilátoru C3183](compiler-error-c3183.md)|nelze definovat nepojmenované třída, struktura nebo sjednocení uvnitř typu spravované/WinRT '*třída*.|
|C3184 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3185](compiler-error-c3185.md)|'ID typu': používat na spravované nebo WinRT typu '*typ*', použijte '*operátor*' místo toho|
|C3186 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3187](compiler-error-c3187.md)|'*identifikátor*': je dostupná jenom v tělo funkce|
|C3188 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3189](compiler-error-c3189.md)|' typeid <*deklarátor*>': Tato syntaxe je už nepodporuje, use::typeid místo ní|
|[Chyba kompilátoru C3190](compiler-error-c3190.md)|'*deklarátor*'s argumenty zadané šablony není explicitní vytvoření instance všechny funkce člen'*typu*.|
|C3191 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3192](compiler-error-c3192.md)|Chyba syntaxe: ' ^' není operátor předpony (měli jste na mysli ' *'?)|
|C3193 chyby kompilátoru|'*vytvořit*': vyžaduje se / clr' nebo ' / ZW se možnost příkazového řádku|
|[Chyba kompilátoru C3194](compiler-error-c3194.md)|'*typ*': typ hodnoty nemůže mít operátor přiřazení|
|[Chyba kompilátoru C3195](compiler-error-c3195.md)|'*– klíčové slovo*': je vyhrazena a nelze použít jako člena třídy nebo hodnota typu ref. Operátory CLR nebo WinRT musí být definován pomocí klíčového slova 'operátor'|
|[Chyba kompilátoru C3196](compiler-error-c3196.md)|'*identifikátor*': používá více než jednou.|
|[Chyba kompilátoru C3197](compiler-error-c3197.md)|'*– klíčové slovo*': lze použít pouze v definicích|
|[Chyba kompilátoru C3198](compiler-error-c3198.md)|Neplatné použití s plovoucí desetinnou čárkou direktivy: fenv_access – Direktiva pragma funguje pouze v režimu přesné|
|[Chyba kompilátoru C3199](compiler-error-c3199.md)|Neplatné použití s plovoucí desetinnou čárkou direktivy: výjimky nejsou podporované v režimu bez přesné|
