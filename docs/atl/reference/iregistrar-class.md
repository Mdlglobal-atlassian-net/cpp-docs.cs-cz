---
title: Rozhraní IRegistrar
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329468"
---
# <a name="iregistrar-interface"></a>Rozhraní IRegistrar

Toto rozhraní je definováno v souboru atliface.h a interně jej používají členské funkce CAtlModule, například [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Syntaxe

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Poznámky

Další podrobnosti najdete v tématu [Using Replaceable Parameters (Preprocessor registrátora).](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Registruje prostředek. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Zruší registraci prostředku.|
|[IRegistrar::Registr souborů](#fileregister)|Zaregistruje soubor.|
|[IRegistrar::SouborUnunregister](#fileunregister)|Zruší registraci souboru.|
|[IRegistrar::StringRegister](#stringregister)|Zaregistruje řetězec.|
|[IRegistrar::StringUnregister](#stringunregister)|Zruší registrace řetězce.|
|[IRegistrar::ResourceRegister](#resourceregister)|Registruje prostředek.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Zruší registraci prostředku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

Registruje prostředek.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

Zruší registraci prostředku.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>IRegistrar::Registr souborů

Zaregistruje soubor.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>IRegistrar::SouborUnunregister

Zruší registraci souboru.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar::StringRegister

Registruje zadaná data řetězce.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>IRegistrar::StringUnregister

Zruší registraci zadaná data řetězce.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>IRegistrar::ResourceRegister

Registruje prostředek.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>IRegistrar::ResourceUnregister

Zruší registraci prostředku.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Viz také

[Použití vyměnitelných parametrů (preprocesor registrátora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)<br/>
[Součást registru (registrátor)](../../atl/atl-registry-component-registrar.md)
