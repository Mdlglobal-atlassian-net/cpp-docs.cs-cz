---
title: Chyby kompilátoru C3100 až C3199
ms.date: 11/17/2017
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
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: 72228be503cee9b080ae667f36b042af88161894
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481871"
---
# <a name="compiler-errors-c3100-through-c3199"></a>Chyby kompilátoru C3100 až C3199

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C3100](compiler-error-c3100.md)|"*identifikátor*': Neznámý kvalifikátor atributu|
|[Chyba kompilátoru C3101](compiler-error-c3101.md)|Neplatný výraz pro argument pojmenovaného atributu '*identifikátor*.|
|C3102 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3103](compiler-error-c3103.md)|"*identifikátor*': opakovaný pojmenovaný argument|
|[Chyba kompilátoru C3104](compiler-error-c3104.md)|Neplatný argument atributu|
|C3105 chyby kompilátoru|"*symbol*': nelze použít jako atribut|
|[Chyba kompilátoru C3106](compiler-error-c3106.md)|"*atribut*': nepojmenovaným argumentům musí předcházet pojmenované argumenty|
|C3107 chyby kompilátoru|"*atribut*': nelze definovat členské funkce nativních atributů|
|C3108 chyby kompilátoru|Typ nejde odvodit, protože seznam inicializátorů není výraz|
|C3109 chyby kompilátoru|"*identifikátor*': metody rozhraní musí používat konvenci volání __cdecl nebo: __stdcall.|
|[Chyba kompilátoru C3110](compiler-error-c3110.md)|"*funkce*': nejde přetížit metodu rozhraní COM.|
|C3111 chyby kompilátoru|Seznam inicializátorů nejde používat jako výchozí argument pro parametr šablony|
|C3112 chyby kompilátoru|"*rozhraní*': rozhraní může deklarovat pouze globální nebo obor názvů|
|[Chyba kompilátoru C3113](compiler-error-c3113.md)|'rozhraní nebo výčet' nemůže být šablona nebo obecná|
|[Chyba kompilátoru C3114](compiler-error-c3114.md)|"*identifikátor*': nejde o platný pojmenovaný argument atributu|
|[Chyba kompilátoru C3115](compiler-error-c3115.md)|"*atribut*': Tento atribut není povolený u"*vytvořit*.|
|[Chyba kompilátoru C3116](compiler-error-c3116.md)|"*specifikátor*': Neplatná třída úložiště pro metodu rozhraní|
|[Chyba kompilátoru C3117](compiler-error-c3117.md)|"*rozhraní*': rozhraní může mít pouze jednu základní třídu|
|[Chyba kompilátoru C3118](compiler-error-c3118.md)|"*rozhraní*': rozhraní nepodporují virtuální dědění|
|C3119 chyby kompilátoru|možnost alignas(void) není povolená|
|[Chyba kompilátoru C3120](compiler-error-c3120.md)|"*identifikátor*': metody rozhraní nemůže převzít seznam argumentů s proměnnou délkou|
|[Chyba kompilátoru C3121](compiler-error-c3121.md)|nejde změnit GUID pro třídu*třídy*.|
|C3122 chyby kompilátoru|"*rozhraní*': Obecné rozhraní WinRT nemůže mít GUID|
|C3123 chyby kompilátoru|Obecné rozhraní WinRT nemůže mít omezení|
|C3124 chyby kompilátoru|'signed char' není platný datový typ WinRT. Místo toho použijte "unsigned char", "wchar_t" nebo "signed short".|
|C3125 chyby kompilátoru|"*typ*': typ nejde přímo nebo nepřímo odvozovat z: Platform::Exception.|
|[Chyba kompilátoru C3126](compiler-error-c3126.md)|nejde definovat sjednocení "*sjednocení*"v rámci spravované/WinRT type'*typ*.|
|C3127 chyby kompilátoru|"*typ*": "*vlastností*' vlastnost jde použít jenom na WinRT ref class|
|C3128 chyby kompilátoru|"*typ*"nemá tabulku vtable, který byl zavedený"*typ*.|
|C3129 chyby kompilátoru|"*typ*': __default_vptr_for_base lze použít pouze na místně definované polymorfní typy a třídy Base|
|[Chyba kompilátoru C3130](compiler-error-c3130.md)|Vnitřní chyba kompilátoru: nepovedlo se zapsat vložený blok kódu do souboru PDB|
|[Chyba kompilátoru C3131](compiler-error-c3131.md)|Projekt musí mít atribut 'module' s vlastností name.|
|[Chyba kompilátoru C3132](compiler-error-c3132.md)|"*parametr*': pole parametrů může používat jedině pro formální argument typu"jednorozměrné pole spravovaných/WinRT.|
|[Chyba kompilátoru C3133](compiler-error-c3133.md)|Atributy nelze použít pro funkce varargs jazyka C++|
|[Chyba kompilátoru C3134](compiler-error-c3134.md)|"*hodnotu*': hodnota argumentu atributu '*argument*"nemá platný typ"*typ*"|
|[Chyba kompilátoru C3135](compiler-error-c3135.md)|"*identifikátor*': vlastnost nemůže mít 'const' nebo zadejte typu volatile.|
|[Chyba kompilátoru C3136](compiler-error-c3136.md)|"*rozhraní*': rozhraní modelu COM může dědit jedině z jiného rozhraní COM"*rozhraní*"není rozhraní modelu COM|
|[Chyba kompilátoru C3137](compiler-error-c3137.md)|"*identifikátor*': vlastnost nelze inicializovat.|
|[Chyba kompilátoru C3138](compiler-error-c3138.md)|"*identifikátor*': '*atribut*" rozhraní musí dědit z rozhraní IDispatch nebo z rozhraní, která dědí z rozhraní IDispatch|
|[Chyba kompilátoru C3139](compiler-error-c3139.md)|"*typ*': nejde vyexportovat UDT bez členů|
|[Chyba kompilátoru C3140](compiler-error-c3140.md)|ve stejné jednotce kompilace nemůže mít víc atributů module.|
|[Chyba kompilátoru C3141](compiler-error-c3141.md)|"*rozhraní*': rozhraní podporují jenom dědění typu public|
|[Chyba kompilátoru C3142](compiler-error-c3142.md)|"*vlastnost*': Nelze převzít adresu proměnné vlastnost|
|C3143 chyby kompilátoru|"*argument*': argument atributu nemůže mít více hodnot|
|C3144 chyby kompilátoru|"*atribut*': atribut vyžaduje explicitní argumenty '*argument*" nepojmenovaný|
|[Chyba kompilátoru C3145](compiler-error-c3145.md)|"*identifikátor*': globální nebo statická proměnná nemůže být typu spravované/WinRT"*typ*.|
|C3146 chyby kompilátoru|Zastaralé.|
|C3147 chyby kompilátoru|Zastaralé.|
|C3148 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3149](compiler-error-c3149.md)|"*typ*': nelze použít tento typ tady bez na nejvyšší úrovni"*token*"|
|[Chyba kompilátoru C3150](compiler-error-c3150.md)|"*vytvořit*": "*atribut*" může používat jedině pro třídu, strukturu, rozhraní, pole nebo ukazatel|
|C3151 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3152](compiler-error-c3152.md)|"*funkce*": "*– klíčové slovo*" může používat jedině pro třídu, strukturu nebo virtuální členská funkce|
|[Chyba kompilátoru C3153](compiler-error-c3153.md)|"*rozhraní*': Nelze vytvořit instanci rozhraní|
|[Chyba kompilátoru C3154](compiler-error-c3154.md)|Byl očekáván ',' před třemi tečkami. Čárkou oddělený tlačítko se třemi tečkami není podporováno ve funkcích pole parametrů.|
|[Chyba kompilátoru C3155](compiler-error-c3155.md)|atributy nejsou v indexeru vlastností povolené.|
|[Chyba kompilátoru C3156](compiler-error-c3156.md)|"*třídy*': nelze mít lokální definici typu spravované/WinRT|
|[Chyba kompilátoru C3157](compiler-error-c3157.md)|Atribut ParamArray dá používat jedině pro poslední parametr|
|C3158 chyby kompilátoru|"*funkce*": "*– klíčové slovo*" může používat jedině pro virtuální členskou funkci|
|[Chyba kompilátoru C3159](compiler-error-c3159.md)|"*identifikátor*': nelze použít deklaraci pole ukazatelů na hodnotový typ.|
|[Chyba kompilátoru C3160](compiler-error-c3160.md)|"*typ*!: datový člen třídy spravované/WinRT nemůže mít tento typ.|
|[Chyba kompilátoru C3161](compiler-error-c3161.md)|"*rozhraní*': vnoření třídy, struktury nebo rozhraní v rozhraní je neplatné; vnoření rozhraní ve třídě nebo struktuře je neplatné|
|[Chyba kompilátoru C3162](compiler-error-c3162.md)|"*typ*': typ odkazu, který má destruktor nelze použít jako typ statického datového členu '*člen*.|
|[Chyba kompilátoru C3163](compiler-error-c3163.md)|"*třídy*': atributy nejsou konzistentní s předchozí deklarací.|
|C3164 chyby kompilátoru|Zastaralé.|
|C3165 chyby kompilátoru|"*hodnotu*': nelze převést na hodnotu s plovoucí desetinnou čárkou nebo celočíselné bod|
|[Chyba kompilátoru C3166](compiler-error-c3166.md)|Zastaralé. "*typ*!: datový člen třídy spravované/WinRT nemůže mít typ"*pointer_type* na vnitřní *managed_pointer_type*"|
|[Chyba kompilátoru C3167](compiler-error-c3167.md)|Nepovedlo se inicializovat rozhraní .NET Framework: Ujistěte se, že je nainstalovaná|
|[Chyba kompilátoru C3168](compiler-error-c3168.md)|"*typ*': Neplatný podkladový typ pro výčet|
|C3169 chyby kompilátoru|"*typ*': nelze odvodit typ pro 'auto' z '*typ*"|
|[Chyba kompilátoru C3170](compiler-error-c3170.md)|v projektu nemůžete mít rozdílné identifikátory modulu.|
|[Chyba kompilátoru C3171](compiler-error-c3171.md)|"*modulu*': nelze specifikovat odlišné atributy module v projektu|
|[Chyba kompilátoru C3172](compiler-error-c3172.md)|"*identifikátor*': nelze zadat jiné atributy idl_module v projektu|
|[Chyba kompilátoru C3173](compiler-error-c3173.md)|Neshoda verzí ve sloučení idl|
|[Chyba kompilátoru C3174](compiler-error-c3174.md)|nebyl zadaný atribut Module|
|[Chyba kompilátoru C3175](compiler-error-c3175.md)|"*funkce*': nelze volat metodu spravovaného typu z nespravované funkce"*funkce*"|
|[Chyba kompilátoru C3176](compiler-error-c3176.md)|"*typ*': nelze deklarovat lokální typ hodnoty|
|C3177 chyby kompilátoru|Nemůžete mít převodní funkci na typ, který obsahuje '*typ*.|
|C3178 chyby kompilátoru|"*typ*': ParamArray nejde používat ve funkci s výchozími argumenty|
|[Chyba kompilátoru C3179](compiler-error-c3179.md)|Nepojmenovaný typ spravovaného/WinRT není povolený.|
|[Chyba kompilátoru C3180](compiler-error-c3180.md)|"*typ*': název překračuje limit metadat '*číslo*" znaky|
|[Chyba kompilátoru C3181](compiler-error-c3181.md)|"*typ*': Neplatný operand pro *– operátor*|
|[Chyba kompilátoru C3182](compiler-error-c3182.md)|"*typ*': deklaraci using-declaration nebo přístup člena je neplatný v rámci typu spravované/WinRT|
|[Chyba kompilátoru C3183](compiler-error-c3183.md)|nelze definovat bez názvu třídy, struktury nebo sjednocení uvnitř typu spravované/WinRT "*třídy*.|
|C3184 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3185](compiler-error-c3185.md)|'ID typu': používá u typu spravované/WinRT "*typ*", použijte "*– operátor*" místo toho|
|C3186 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3187](compiler-error-c3187.md)|"*identifikátor*": je dostupné jenom v těle funkce|
|C3188 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3189](compiler-error-c3189.md)|"typeid <*deklarátor*>': Tato syntaxe už není podporovaná, operátor:: typeid místo|
|[Chyba kompilátoru C3190](compiler-error-c3190.md)|"*deklarátor*"se zadanými argumenty šablony není explicitní vytváření instancí žádné členské funkce"*typ*.|
|C3191 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3192](compiler-error-c3192.md)|Chyba syntaxe: ' ^' není prefixový operátor (měli jste na mysli ' *'?)|
|C3193 chyby kompilátoru|"*vytvořit*": vyžaduje "/ clr' nebo ' / ZW' možnost příkazového řádku|
|[Chyba kompilátoru C3194](compiler-error-c3194.md)|"*typ*': hodnotový typ nemůže mít operátor přiřazení|
|[Chyba kompilátoru C3195](compiler-error-c3195.md)|"*– klíčové slovo*": je vyhrazené a nejde použít jako člen ref class nebo hodnotového typu. Operátory CLR/WinRT musí být definovány pomocí klíčového slova operator.|
|[Chyba kompilátoru C3196](compiler-error-c3196.md)|"*identifikátor*': používá více než jednou.|
|[Chyba kompilátoru C3197](compiler-error-c3197.md)|"*– klíčové slovo*': jde použít jenom v definicích|
|[Chyba kompilátoru C3198](compiler-error-c3198.md)|Neplatné použití direktiv pragma s plovoucí desetinnou čárkou: Direktiva pragma fenv_access funguje jedině v režimu přesné|
|[Chyba kompilátoru C3199](compiler-error-c3199.md)|Neplatné použití direktiv pragma s plovoucí desetinnou čárkou: výjimky jsou podporované jedině v režimu bez přesné|
