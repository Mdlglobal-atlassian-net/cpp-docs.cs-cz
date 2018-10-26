---
title: Zařazení globálních funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0b9a8e72cb3c1334484ed4a4e5c85c8b9a12347
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055135"
---
# <a name="marshaling-global-functions"></a>Zařazení globálních funkcí

Tyto funkce poskytují podporu pro zařazování a převodem zařazování dat na ukazatele rozhraní.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Uvolní zařazování dat a `IStream` ukazatele.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Vytvoří nový objekt streamu a zařadí zadaný ukazatel rozhraní.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Převede zařazovaná data streamu ukazatel rozhraní.|

## <a name="requirements"></a>Požadavky:

**Záhlaví:** atlbase.h

##  <a name="atlfreemarshalstream"></a>  AtlFreeMarshalStream

Uvolní zařazování dat ve streamu a následně uvolní ukazatel streamu.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Ukazatel `IStream` rozhraní na datový proud použitý k zařazování.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [AtlMarshalPtrInProc](#atlmarshalptrinproc).

##  <a name="atlmarshalptrinproc"></a>  AtlMarshalPtrInProc

Vytvoří nový objekt streamu, zapíše do tohoto streamu identifikátor CLSID proxy a zařadí zadaný ukazatel rozhraní tím, že do streamu zapíše data potřebná k inicializaci proxy.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel rozhraní k zařadit.

*identifikátor IID*<br/>
[in] Identifikátor GUID rozhraní se zařadit.

*ppStream*<br/>
[out] Ukazatel `IStream` rozhraní u nového objektu datového proudu, který se používá pro zařazování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Příznak MSHLFLAGS_TABLESTRONG je nastaven tak, že ukazatele může být zařazen do různých datových proudů. Ukazatel může být také zařazeny více než jednou.

Pokud zařazování selže, se uvolní ukazatel streamu.

`AtlMarshalPtrInProc` jde použít jenom na ukazatel na objekt v rámci procesu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

##  <a name="atlunmarshalptr"></a>  AtlUnmarshalPtr

Převede zařazovaná data streamu na ukazatel rozhraní, který může použít klient.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Ukazatel na datový proud se zařazeny.

*identifikátor IID*<br/>
[in] Identifikátor GUID rozhraní jsou zařazeny.

*ppUnk*<br/>
[out] Ukazatel na rozhraní zrušeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)
