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
ms.openlocfilehash: d05af932d5f531a4dab02e7e0ca171f4484891a3
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556319"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl – třída

Poskytuje implementaci pro [ICommandText](https://docs.microsoft.com/previous-versions/windows/desktop/ms714914(v=vs.85)) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Příkaz třída odvozená z `ICommandTextImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** altdb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[Getcommandtext –](#getcommandtext)|Vrátí text příkazu nastavil poslední volání [SetCommandText –](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Nastaví text příkazu, nahraďte existující text příkazu.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Slouží k uložení textu příkazu.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní na příkazy.

## <a name="getcommandtext"></a> ICommandTextImpl::GetCommandText

Vrátí text příkazu nastavil poslední volání [SetCommandText –](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobrazit [ICommandText::GetCommandText](https://docs.microsoft.com/previous-versions/windows/desktop/ms709825(v=vs.85)) v *referenční informace pro OLE DB programátory*. *PguidDialect* ve výchozím nastavení je parametr ignorován.

## <a name="setcommandtext"></a> ICommandTextImpl::SetCommandText

Nastaví text příkazu, nahraďte existující text příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobrazit [ICommandText::SetCommandText](https://docs.microsoft.com/previous-versions/windows/desktop/ms709757(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="strcommandtext"></a> ICommandTextImpl::m_strCommandText

Ukládá příkaz textový řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)