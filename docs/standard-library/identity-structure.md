---
title: identity – struktura
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 722eb9c0579d0c07765434127d0a7c43718fbc37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404993"
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

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Hodnota k identifikaci.|

## <a name="remarks"></a>Poznámky

Třída obsahuje definice veřejného typu `type`, což je stejná jako parametr šablony typu. Používá se ve spojení s funkcí šablony [vpřed](../standard-library/utility-functions.md#forward) a ujistěte se, že parametr funkce mají požadovaného typu.

Z důvodu kompatibility se starším kódem, třída také definuje funkci identity `operator()` který vrátí svůj argument *levé*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nástroje >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<Nástroje >](../standard-library/utility.md)<br/>
