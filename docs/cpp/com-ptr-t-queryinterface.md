---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 42953c92e4cf31b5ccd02dd51811fc1fdeedbcaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543829"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface

**Specifické pro Microsoft**

Volání **QueryInterface** členskou funkci `IUnknown` na zapouzdřený ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
`IID` z ukazatele rozhraní.

*p*<br/>
Nezpracovaný ukazatel rozhraní.

## <a name="remarks"></a>Poznámky

Volání `IUnknown::QueryInterface` na zapouzdřený ukazatel rozhraní se zadaným `IID` a vrátí výsledný nezpracovaného ukazatele rozhraní v *p*. Tato rutina vrátí hodnotu HRESULT indikuje úspěch nebo selhání.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)