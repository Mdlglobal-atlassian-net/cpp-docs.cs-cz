---
title: ComPtr::operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 177d6ebde6a4611e9a08dc3dade63bd6c3acc3fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401625"
---
# <a name="comptroperator-operator"></a>ComPtr::operator= – operátor

Přiřadí hodnotu k aktuální **ComPtr**.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)  
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Třída.

*Ostatní*<br/>
Ukazatel, odkaz nebo odkaz rvalue na typ nebo jiný **ComPtr**.

## <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální **ComPtr**.

## <a name="remarks"></a>Poznámky

První verze tohoto operátoru přiřadí aktuální prázdnou hodnotu **ComPtr**.

V druhém verzi, pokud přiřazení ukazatel rozhraní není stejný jako aktuální **ComPtr** ukazatel rozhraní, je druhý ukazatel rozhraní je přiřazen k aktuální **ComPtr**.

Ve třetí verzi je přiřazení ukazatel rozhraní přiřazená aktuální **ComPtr**.

Ve čtvrtém verzi, pokud ukazatel rozhraní přiřazování hodnot není stejný jako aktuální **ComPtr** ukazatel rozhraní, je druhý ukazatel rozhraní je přiřazen k aktuální **ComPtr**.

Je pátá verze kopírovacího operátoru; odkaz na **ComPtr** je přiřazen k aktuální **ComPtr**.

Šestá verze je operátor kopie, která používá přesunutí sémantiky; Odkaz rvalue na **ComPtr** Pokud libovolného typu je statické přetypování a posléze přiřazeny k aktuální **ComPtr**.

Sedmý verze je operátor kopie, která používá přesunutí sémantiky; Odkaz rvalue na **ComPtr** typu *U* je statické přetypování pak a přiřazeny k aktuální **ComPtr**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)