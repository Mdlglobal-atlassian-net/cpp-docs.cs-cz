---
title: Zařazování globálních funkcí
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326264"
---
# <a name="marshaling-global-functions"></a>Zařazování globálních funkcí

Tyto funkce poskytují podporu pro zařazování a převod dat zařazování do ukazatelů rozhraní.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Uvolní data marshal a `IStream` ukazatel.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Vytvoří nový objekt datového proudu a zařazuje zadaný ukazatel rozhraní.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Převede data zařazování datového proudu na ukazatel rozhraní.|

## <a name="requirements"></a>Požadavky:

**Záhlaví:** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream

Uvolní zařazování dat ve streamu a následně uvolní ukazatel streamu.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[v] Ukazatel na `IStream` rozhraní v datovém proudu slouží pro zařazování.

### <a name="example"></a>Příklad

Viz příklad pro [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc

Vytvoří nový objekt streamu, zapíše do tohoto streamu identifikátor CLSID proxy a zařadí zadaný ukazatel rozhraní tím, že do streamu zapíše data potřebná k inicializaci proxy.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na rozhraní, které má být zařazeno.

*Iid*<br/>
[v] Identifikátor GUID rozhraní, které je zařazováno.

*Ppstream*<br/>
[out] Ukazatel na `IStream` rozhraní na nový objekt datového proudu, který se používá pro zařazování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Příznak MSHLFLAGS_TABLESTRONG je nastaven tak, aby ukazatel může být zařazen do více datových proudů. Ukazatel může být také unmarshaled vícekrát.

Pokud zařazování selže, je uvolněn ukazatel datového proudu.

`AtlMarshalPtrInProc`lze použít pouze na ukazatel na objekt v procesu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr

Převede zařazovaná data streamu na ukazatel rozhraní, který může použít klient.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[v] Ukazatel na nezařazený datový proud.

*Iid*<br/>
[v] Identifikátor GUID rozhraní, které je unmarshaled.

*ppUnk*<br/>
[out] Ukazatel na nezařazené rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

Viz příklad pro [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
