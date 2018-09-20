---
title: Module::registercomobject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7cccebf6e1c6004a2416f4fdeb254369f9aa7b72
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410309"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject – metoda

Zaregistruje jeden nebo více objektů modelu COM, takže k nim mohli připojit další aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);

```

### <a name="parameters"></a>Parametry

*název_serveru*<br/>
Plně kvalifikovaný název serveru.

*CLSID*<br/>
Pole CLSID k registraci.

*objekty pro vytváření*<br/>
Pole rozhraní IUnknown objektů tříd, jejichž dostupnost je publikován.

*Soubory cookie*<br/>
Po dokončení operace, pole ukazatelů na hodnoty, které identifikují třídu objektů, které jste zaregistrovali. Tyto hodnoty se později použijí zrušit registraci.

*Počet*<br/>
Počet CLSID k registraci.

## <a name="return-value"></a>Návratová hodnota

S_OK Pokud úspěšné; v opačném případě HRESULT jako je například CO_E_OBJISREG, který označuje důvod operace se nezdařila.

## <a name="remarks"></a>Poznámky

Objekty modelu COM jsou registrovány CLSCTX_LOCAL_SERVER enumerátor výčtu CLSCTX.

Typ připojení k registrované objekty je určená kombinací aktuální *comflag* parametr šablony a REGCLS_SUSPENDED enumerátor výčtu REGCLS.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)