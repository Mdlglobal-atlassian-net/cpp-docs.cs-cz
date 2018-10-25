---
title: runtime_checks – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs:
- C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72dadf249149309b58031ad99ad28941a3f88d59
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073819"
---
# <a name="runtimechecks"></a>runtime_checks
Zakáže nebo obnoví [/RTC](../build/reference/rtc-run-time-error-checks.md) nastavení.

## <a name="syntax"></a>Syntaxe

```
#pragma runtime_checks( "[runtime_checks]", {restore | off} )
```

## <a name="remarks"></a>Poznámky

Nelze povolit kontrolu za běhu, který není povolená s možností kompilátoru. Například, pokud nezadáte `/RTCs`, zadání `#pragma runtime_checks( "s", restore)` neumožní ověřování rámců zásobníku.

**Runtime_checks –** – Direktiva pragma musí být uvedena mimo funkci a na první funkci definovanou po viděli direktivy pragma se projeví. *Obnovení* a *vypnout* argumenty zapnutí možnosti zadané v **runtime_checks –** zapnutí nebo vypnutí.

**Runtime_checks –** může být nula nebo více parametrů je znázorněno v následující tabulce.

### <a name="parameters-of-the-runtimechecks-pragma"></a>Parametry runtime_checks – direktiva Pragma

|Parametry|Typ kontroly za běhu|
|--------------------|-----------------------------|
|*s*|Umožňuje seskupit ověření (snímek).|
|*c*|Oznámí, že na menší datový typ, který vede ke ztrátě dat je přiřazena hodnota.|
|*u*|Oznámí, pokud se nějaká proměnná použije předtím, než se definuje.|

Toto jsou stejná písmena použít s `/RTC` – možnost kompilátoru. Příklad:

```
#pragma runtime_checks( "sc", restore )
```

Použití **runtime_checks –** – Direktiva pragma se prázdný řetězec (**""**) je zvláštní forma direktivy:

- Při použití *vypnout* parametr, ukazuje kontroly chyb za běhu, uvedené v tabulce výše, vypnuto.

- Při použití *obnovení* parametr resetuje kontroly chyb za běhu na ty, které jste zadali pomocí `/RTC` – možnost kompilátoru.

```
#pragma runtime_checks( "", off )
.
.
.
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)