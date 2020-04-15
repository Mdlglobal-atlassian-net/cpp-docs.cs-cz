---
title: IsBaseOfStrict – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371357"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*Základní*<br/>
Základní typ.

*Odvozené*<br/>
Odvozený typ.

## <a name="remarks"></a>Poznámky

Testuje, zda jeden typ je základem jiného.

První šablona testuje, zda je typ odvozen ze základního typu, který může přinést **hodnotu true** nebo **false**. Druhá šablona testuje, zda je typ odvozen od sebe sama, což vždy dává **false**.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

Name (Název)                            | Popis
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::hodnota](#value) | Označuje, zda jeden typ je základem jiného.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsBaseOfStrict`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="isbaseofstrictvalue"></a><a name="value"></a>IsBaseOfStrict::hodnota

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Poznámky

Označuje, zda jeden typ je základem jiného.

`value`**true,** pokud `Base` je typ základní `Derived`třídou typu , jinak je **false**.
