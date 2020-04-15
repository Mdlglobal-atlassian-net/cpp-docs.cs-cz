---
title: DontUseNewUseMake – třída
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371557"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Poznámky

Zabraňuje použití `new` operátoru v . `RuntimeClass` V důsledku toho je nutné použít [make funkce](make-function.md) místo.

## <a name="members"></a>Členové

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                             | Popis
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operátor nový](#operator-new) | Přetížení operátor `new` a zabraňuje jeho použití `RuntimeClass`v .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DontUseNewUseMake`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>DontUseNewUseMake::operátor nový

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parametry

*__unnamed0*<br/>
Nepojmenovaný parametr, který určuje počet bajtů paměti, které mají být přiděleny.

*Umístění*<br/>
Typ, který má být přidělen.

### <a name="return-value"></a>Návratová hodnota

Poskytuje způsob, jak předat další argumenty, pokud přetížení operátor `new`.

### <a name="remarks"></a>Poznámky

Přetížení operátor `new` a zabraňuje jeho použití `RuntimeClass`v .
