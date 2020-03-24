---
title: _bstr_t::wchar_t *, _bstr_t::char*
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: 5fdce29b0be7e9aabae9e3c602822045a7bccafd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190297"
---
# <a name="_bstr_twchar_t-_bstr_tchar"></a>_bstr_t::wchar_t\*, _bstr_t::char\*

**Specifické pro společnost Microsoft**

Vrátí znaky BSTR jako pole širokých nebo úzkých znaků.

## <a name="syntax"></a>Syntaxe

```
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>Poznámky

Tyto operátory lze použít k extrahování textových dat, která jsou zapouzdřena objektem `BSTR`. Přiřazení nové hodnoty vrácenému ukazateli nezmění původní data BSTR.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
