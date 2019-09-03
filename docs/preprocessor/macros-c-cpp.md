---
title: Makra (C/C++)
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: ba2c0f012974a528876219d00c61c0f31a6cd820
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218858"
---
# <a name="macros-cc"></a>Makra (C/C++)

Preprocesor rozbalí makra na všech řádcích kromě *direktiv preprocesoru*, řádků, které mají **#** jako první neprázdný znak. Rozbalí makra v částech některých direktiv, které nejsou přeskočeny jako součást podmíněné kompilace. *Direktivy podmíněné kompilace* umožňují potlačit kompilaci částí zdrojového souboru. Testuje konstantní výraz nebo identifikátor k určení, které textové bloky mají být předávány kompilátoru a které mají být odebrány ze zdrojového souboru během předběžného zpracování.

Direktiva `#define` je obvykle použita pro přiřazení smysluplných identifikátorů konstantám, klíčovým slovům a běžně používaným příkazům a výrazům. Identifikátory, které představují konstanty, jsou někdy označovány jako *symbolické konstanty* nebo *konstanty manifestu*. Identifikátory, které představují příkazy nebo výrazy, se nazývají *makra*. V této dokumentaci preprocesoru se používá pouze termín „makro“.

Pokud je název makra rozpoznán ve zdrojovém textu programu nebo v argumentech určitých dalších příkazů preprocesoru, je považován za volání tohoto makra. Název makra je nahrazen kopií těla makra. Pokud makro přijímá argumenty, jsou v těle makra argumenty za názvem makra nahrazeny skutečnými parametry. Proces nahrazení volání makra za zpracovávanou kopii těla se nazývá *rozšíření* volání makra.

V praxi existují dva typy maker. Makra *podobné objektům* nevyužívají žádné argumenty. Makra *podobná funkci* mohou být definována pro přijímání argumentů, aby vypadaly a fungovaly jako volání funkcí. Vzhledem k tomu, že makra negenerují skutečná volání funkce, můžete někdy rychlejší spouštění programů nahrazením volání funkce pomocí maker. (V jazyce C++ jsou často upřednostňovanou metodou vložené funkce.) Makra však mohou vytvářet problémy, pokud je nedefinujete a nepoužíváte je pečlivě. U definice maker bude možná zapotřebí používat závorky spolu s argumenty, aby bylo možné zachovat správnou prioritu ve výrazu. Makra také nemusí správně zpracovávat výrazy s vedlejšími účinky. Další informace najdete `getrandom` v příkladu v direktivě [#define](../preprocessor/hash-define-directive-c-cpp.md).

Po definování makra ji nemůžete znovu definovat na jinou hodnotu, aniž by bylo nutné původní definici odebrat. Je však možné předefinovat makro stejnou definicí. Proto se stejná definice může v programu objevit více než jednou.

`#undef` Direktiva odstraní definici makra. Po odebrání definice můžete makro znovu definovat na jinou hodnotu. Direktiva [#define](../preprocessor/hash-define-directive-c-cpp.md) a [Direktiva #undef](../preprocessor/hash-undef-directive-c-cpp.md) projednávají `#define` direktivy a `#undef` v uvedeném pořadí.

Další informace najdete v tématu.

- [Makra a jazyk C++](../preprocessor/macros-and-cpp.md)

- [Variadická makra](../preprocessor/variadic-macros.md)

- [Předdefinovaná makra](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>Viz také:

[C/C++ reference preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)
