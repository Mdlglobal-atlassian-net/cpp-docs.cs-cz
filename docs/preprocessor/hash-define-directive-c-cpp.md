---
title: '##define – direktiva (C/C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#define'
dev_langs:
- C++
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8875c2b2c744a16f936fd2220826f23413a0e6c9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="define-directive-cc"></a>#define – direktiva (C++)
`#define` Vytvoří *makro*, což je identifikátor nebo identifikátor parametrizované přidružení k řetězec tokenu. Po definování makro kompilátor můžete nahradit řetězec tokenu pro každý výskyt identifikátor ve zdrojovém souboru.  
  
## <a name="syntax"></a>Syntaxe  
 `#define` *identifikátor* *token řetězec*opt  
  
 `#define` *identifikátor* `(` *identifikátor*opt`,`*...*  `,` *identifikátor*opt`)`*token řetězec*opt  
  
## <a name="remarks"></a>Poznámky  
 `#define` – Direktiva způsobí, že kompilátor nahraďte *token řetězec* pro každý výskyt *identifikátor* ve zdrojovém souboru. *Identifikátor* je nahrazena jenom v případě, že tvoří token. To znamená *identifikátor* není nahrazena, pokud se zobrazí v komentář, řetězce nebo jako součást identifikátor delší. Další informace najdete v tématu [tokeny](../cpp/tokens-cpp.md).  
  
 *Token řetězec* argument se skládá z řady tokenů, jako jsou klíčová slova, konstanty nebo dokončení příkazy. Jeden nebo více prázdných znaků musí oddělení *token řetězec* z *identifikátor*. Tento prázdný znak není považovány za součást nahrazovanou text, ani je prázdný znak, který následuje poslední token text.  
  
 A `#define` bez *token řetězec* odebere výskyty *identifikátor* ze zdrojového souboru. *Identifikátor* zůstane definované a lze je testovat pomocí `#if defined` a `#ifdef` direktivy.  
  
 Druhý formulář syntaxe definuje makro jako funkce s parametry. Tento formulář je možné zadat volitelný seznam parametrů, které musí být v závorkách. Po výskytu definované, každý další makro *identifikátor*( *identifikátor*opt..., *identifikátor*výslovný) se nahradí verzi  *token řetězec* argument, který má skutečné argumenty nahrazena formální parametrů.  
  
 Formální parametr názvy se zobrazí v *token řetězec* označit umístění, kde jsou nahrazeny skutečnými hodnotami. Název každého parametru může vyskytovat více než jednou. v *token řetězec*, a názvy může objevit v libovolném pořadí. Počet argumentů ve volání musí shodovat s počtem parametrů v definici makra. Volná použití závorek zaručuje správnou interpretaci komplexní skutečných argumentů.  
  
 Formální parametry v seznamu jsou oddělené čárkami. Každý název v seznamu musí být jedinečný, a v seznamu musí být uzavřena v závorkách. Můžete oddělit bez mezer *identifikátor* a levé závorky. Použití řádku zřetězení – umístit zpětné lomítko (`\`) bezprostředně před znak nového řádku – pro dlouho direktivy na více řádků zdroje. Obor názvů formální parametr rozšiřuje na nový řádek, který končí *token řetězec*.  
  
 Při makra byla definována v druhý formulář syntaxe, následné textovou instance, za nímž následuje seznam argumentů znamenat makro volání. Skutečné argumenty, které následuje instanci *identifikátor* ve zdrojovém souboru, které se shodují se odpovídající formální parametry v definici makra. Každý formální parametr v *token řetězec* , není sebou nastavení velikosti řetězce (`#`), charakterizace (`#@`), nebo vložení tokenu (`##`) operátor, nebo není následované `##` operátor, je nahrazuje odpovídající skutečné argument. Makra v skutečné argumentu jsou rozšířit před direktiva nahrazuje formální parametr. (Operátory jsou popsány v [preprocesor operátory](../preprocessor/preprocessor-operators.md).)  
  
 Následující příklady makra s argumenty ilustrují o druhou podobu `#define` syntaxe:  
  
```  
// Macro to define cursor lines   
#define CURSOR(top, bottom) (((top) << 8) | (bottom))  
  
// Macro to get a random integer with a specified range   
#define getrandom(min, max) \  
    ((rand()%(int)(((max) + 1)-(min)))+ (min))  
```  
  
 Argumenty s vedlejšími účinky někdy způsobit maker, pro vést k neočekávaným výsledkům. Daný formální parametr může být uveden více než jednou v *token řetězec*. Pokud je tento formální parametr je nahrazena výraz s vedlejšími účinky, výraz s vedlejšími účinky, může vyhodnotí více než jednou. (Podívejte se na příklady pod [operátor vložení tokenu (##)](../preprocessor/token-pasting-operator-hash-hash.md).)  
  
 `#undef` – Direktiva způsobí, že je identifikátor preprocesoru definici tak, aby se zapomenete. V tématu [#undef – direktiva](../preprocessor/hash-undef-directive-c-cpp.md) Další informace.  
  
 Pokud název makra definovaný dojde v *token řetězec* (i v důsledku jiné rozšíření makro), není rozbalen.  
  
 Druhý `#define` pro makro se stejným názvem generuje upozornění, pokud druhé tokenu pořadí je stejný jako první.  
  
 **Konkrétní Microsoft**  
  
 Microsoft C/C++ umožňuje znovu definovat makra, pokud je syntakticky stejný jako původní definici novou definici. Jinými slovy dvě definice může mít jiný parametr názvy. Toto chování se liší od [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] C, která vyžaduje, aby dvě definice lexikálně identické.  
  
 Například následující dvě makra jsou identické s výjimkou názvy parametrů. [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] C nepovoluje takové předefinování, ale Microsoft C/C++ zkompiluje ho bez chyby.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( a1 * a2 )  
```  
  
 Na druhé straně následující dvě makra nejsou identické a vygeneruje upozornění v Microsoft C/C++.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( b1 * b2 )  
```  
  
 **Konkrétní Microsoft END**  
  
 Tento příklad ukazuje `#define` – direktiva:  
  
```  
#define WIDTH       80  
#define LENGTH      ( WIDTH + 10 )  
```  
  
 První příkaz definuje identifikátor `WIDTH` jako celé číslo konstantní 80 a definuje `LENGTH` z hlediska `WIDTH` a konstantní 10 na celé číslo. Každý výskyt `LENGTH` je nahrazena (`WIDTH + 10`). V zapnout každý výskyt `WIDTH + 10` je nahrazena výraz (`80 + 10`). Závorky `WIDTH + 10` jsou důležité, protože se řídí se výklad v příkazech, jako je následující:  
  
```  
var = LENGTH * 20;  
```  
  
 Po předběžném zpracování Příprava příkaz změní na:  
  
```  
var = ( 80 + 10 ) * 20;  
```  
  
 která se vyhodnotí jako 1 800. Bez závorek výsledkem je:  
  
```  
var = 80 + 10 * 20;  
```  
  
 která se vyhodnotí jako 280.  
  
 **Konkrétní Microsoft**  
  
 Definice makra a konstant s [/D](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru má stejný účinek jako použití `#define` předběžného zpracování direktiva na začátku souboru. Až 30 makra lze definovat pomocí možnosti /D.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)