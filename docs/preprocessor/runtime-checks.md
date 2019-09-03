---
title: runtime_checks – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: a1c8e6cca27e157818e6ec80182f8fefa112daf1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216618"
---
# <a name="runtime_checks-pragma"></a>runtime_checks – direktiva pragma

Zakáže nebo obnoví nastavení [/RTC](../build/reference/rtc-run-time-error-checks.md) .

## <a name="syntax"></a>Syntaxe

> **#pragma runtime_checks ("** [ *runtime_checks* ] **";** { **Restore** | **off** } **)**

## <a name="remarks"></a>Poznámky

Nelze povolit kontrolu za běhu, která nebyla povolena možností kompilátoru. Například pokud nezadáte `/RTCs` na příkazovém řádku, zadáním `#pragma runtime_checks( "s", restore)` nepovolíte ověřování snímku zásobníku.

Direktiva pragma **runtime_checks** se musí vyskytovat vně funkce a projeví se v první funkci definované po zobrazení direktivy pragma. Argumenty **Restore** a **off** zapínají možnosti zadané v **runtime_checks** nebo off.

**Runtime_checks** může být nula nebo více parametrů uvedených v následující tabulce.

### <a name="parameters-of-the-runtime_checks-pragma"></a>Parametry direktivy pragma runtime_checks

| Parametr (y) | Typ kontroly za běhu |
|--------------------|-----------------------------|
| **s** | Povolí ověřování zásobníku (Frame). |
| **c** | Vytvoří sestavy, je-li přiřazena hodnota k menšímu datovému typu, který má za následek ztrátu dat. |
| **u** | Hlásí, že je před definováním proměnné použita proměnná. |

Tyto parametry jsou stejné jako používané s `/RTC` možností kompilátoru. Příklad:

```cpp
#pragma runtime_checks( "sc", restore )
```

Použití direktivy pragma **runtime_checks** s prázdným řetězcem ( **""** ) je zvláštní forma direktivy:

- Při použití parametru **off** dojde k vypnutí kontrol chyb za běhu uvedených v tabulce výše.

- Použijete-li parametr Restore, dojde k resetování kontrol chyb za běhu do těch, které jste zadali pomocí `/RTC` možnosti kompilátoru.

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
