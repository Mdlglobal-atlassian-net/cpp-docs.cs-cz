---
title: _com_error::WCodeToHRESULT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b6712734cd7283558ad5776444586f8c0b3fa6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077565"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Specifické pro Microsoft**

Mapuje 16bitové *wCode* 32-bit HRESULT.

## <a name="syntax"></a>Syntaxe

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parametry

*WCode*<br/>
16bitové hodnoty *wCode* namapována na 32bitové HRESULT.

## <a name="return-value"></a>Návratová hodnota

Mapovaná z 16bitové hodnoty HRESULT 32-bit *wCode*.

## <a name="remarks"></a>Poznámky

Zobrazit [WCode](../cpp/com-error-wcode.md) členskou funkci.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error – třída](../cpp/com-error-class.md)