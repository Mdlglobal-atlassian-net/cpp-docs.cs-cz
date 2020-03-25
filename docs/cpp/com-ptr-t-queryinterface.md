---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 26dda2dff83ff0adbb7ef05c5e75f64b44138bd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170668"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Specifické pro společnost Microsoft**

Volá členskou funkci **QueryInterface** `IUnknown` na ukazatel zapouzdřeného rozhraní.

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

*identifikátor*<br/>
`IID` ukazatele rozhraní.

*trub*<br/>
Nezpracovaný ukazatel rozhraní

## <a name="remarks"></a>Poznámky

Volá `IUnknown::QueryInterface` na ukazatel zapouzdřeného rozhraní se zadaným `IID` a vrátí výsledný ukazatel nezpracovaného nezpracovaného rozhraní v *p*. Tato rutina vrátí HRESULT, aby označovala úspěch nebo neúspěch.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
