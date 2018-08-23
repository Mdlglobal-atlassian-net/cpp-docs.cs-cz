---
title: Ftmbase::releasemarshaldata – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
dev_langs:
- C++
helpviewer_keywords:
- ReleaseMarshalData method
ms.assetid: a94f9940-183a-4fde-8504-d223f346a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2d4bccbcd9f3c3b13fa8be0ccc7afa493751cd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593536"
---
# <a name="ftmbasereleasemarshaldata-method"></a>FtmBase::ReleaseMarshalData – metoda

Zničí zařazené datový paket.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parametry

*pStm*  
Ukazatel na datový proud, který obsahuje datový paket, který se má zničit.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[FtmBase – třída](../windows/ftmbase-class.md)