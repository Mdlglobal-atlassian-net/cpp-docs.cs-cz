---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180781"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Specifické pro společnost Microsoft**

Vytvoří objekt **_com_error** .

## <a name="syntax"></a>Syntaxe

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Parametry

*oddělení*<br/>
Informace HRESULT.

*perrinfo*<br/>
objekt `IErrorInfo`.

*fAddRef*<br/>
Výchozí způsobí, že konstruktor volá AddRef na `IErrorInfo` rozhraní, které není null. To poskytuje správné počítání odkazů v běžném případě, kdy je vlastnictví rozhraní předáno do objektu **_com_error** , například:

```cpp
throw _com_error(hr, perrinfo);
```

Pokud nechcete, aby váš kód přenesl vlastnictví do objektu **_com_error** a `AddRef` je vyžadováno pro posunutí `Release` v **_com_error** destruktoru, Sestavte objekt následujícím způsobem:

```cpp
_com_error err(hr, perrinfo, true);
```

*zda*<br/>
Existující objekt **_com_error** .

## <a name="remarks"></a>Poznámky

První konstruktor vytvoří nový objekt s předaným HRESULT a volitelným objektem `IErrorInfo`. Druhý vytvoří kopii existujícího objektu **_com_error** .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_error – třída](../cpp/com-error-class.md)
