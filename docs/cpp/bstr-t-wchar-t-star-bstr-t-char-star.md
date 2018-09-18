---
title: _bstr_t::wchar_t *, _bstr_t::char* | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
dev_langs:
- C++
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abd0b53c178e028b975e2b26d36317b773c2cfa5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102759"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t::wchar_t *, _bstr_t::char*

**Specifické pro Microsoft**

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_bstr_t – třída](../cpp/bstr-t-class.md)