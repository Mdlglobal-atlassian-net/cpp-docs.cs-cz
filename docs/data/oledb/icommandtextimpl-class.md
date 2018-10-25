---
title: Icommandtextimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2ddd7e1a4397b36daba8b354c84941d0d1c4d0e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057969"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl – třída

Poskytuje implementaci pro [ICommandText](/previous-versions/windows/desktop/ms714914) rozhraní.

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

Zobrazit [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825) v *referenční informace pro OLE DB programátory*. *PguidDialect* ve výchozím nastavení je parametr ignorován.

## <a name="setcommandtext"></a> ICommandTextImpl::SetCommandText

Nastaví text příkazu, nahraďte existující text příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect, 
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobrazit [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757) v *referenční informace pro OLE DB programátory*.

## <a name="strcommandtext"></a> ICommandTextImpl::m_strCommandText

Ukládá příkaz textový řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)