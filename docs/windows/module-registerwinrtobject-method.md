---
title: Module::registerwinrtobject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a7f5879a3a76e9af795a5dfc808423b43515662a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609298"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject – metoda

Zaregistruje jeden nebo více objektů prostředí Windows Runtime, takže k nim mohli připojit další aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)  
```

### <a name="parameters"></a>Parametry

*název_serveru*  
Název, který určuje podmnožinu objekty ovlivněné touto operací.

*activatableClassIds*  
Pole aktivovatelné CLSID k registraci.

*Soubor cookie*  
Hodnota, která označuje, které jste zaregistrovali objekty třídy. Tato hodnota se používá později zrušení registrace.

*Počet*  
Počet objektů, které chcete zaregistrovat.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chybu HRESULT jako je například CO_E_OBJISREG, který označuje důvod operace se nezdařila.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
[Module – třída](../windows/module-class.md)