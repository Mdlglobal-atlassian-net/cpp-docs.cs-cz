---
title: identity – struktura
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 49b2c1eb3ca03f9bf9199bdbca49348866ff0a7e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246167"
---
# <a name="identity-structure"></a>identity – struktura

Struktura, která obsahuje definici typu jako parametr šablony.

## <a name="syntax"></a>Syntaxe

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
};
```

### <a name="parameters"></a>Parametry

*doleva*\
Hodnota k identifikaci.

## <a name="remarks"></a>Poznámky

Třída obsahuje definice veřejného typu `type`, což je stejná jako parametr šablony typu. Používá se ve spojení s funkcí šablony [vpřed](../standard-library/utility-functions.md#forward) a ujistěte se, že parametr funkce mají požadovaného typu.

Z důvodu kompatibility se starším kódem, třída také definuje funkci identity `operator()` který vrátí svůj argument *levé*.
