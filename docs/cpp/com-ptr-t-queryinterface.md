---
title: _com_ptr_t::QueryInterface | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0add1d8f3fc73f78cee3e10642d7b5a12968a6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106869"
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