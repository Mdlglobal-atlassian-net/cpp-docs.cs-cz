---
title: ICommandTextImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: d91221dd509122ebbd6490c2de7fab1ce51eb2f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210727"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl – třída

Poskytuje implementaci pro rozhraní [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída příkazu odvozená od `ICommandTextImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** altdb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetCommandText](#getcommandtext)|Vrátí textový příkaz nastavený posledním voláním metody [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Nastaví text příkazu a nahradí stávající text příkazu.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Ukládá text příkazu.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní pro příkazy.

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a>ICommandTextImpl:: GetCommandText

Vrátí textový příkaz nastavený posledním voláním metody [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parametry

Viz [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) v *referenci OLE DB programátora*. Parametr *pguidDialect* se ve výchozím nastavení ignoruje.

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a>ICommandTextImpl:: SetCommandText

Nastaví text příkazu a nahradí stávající text příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parametry

Viz adresu [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a>ICommandTextImpl:: m_strCommandText

Ukládá textový řetězec příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
