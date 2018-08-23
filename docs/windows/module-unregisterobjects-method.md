---
title: Module::unregisterobjects – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ee7e6deeda17d2ac374b39edf70ab28fa1457fa
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603378"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects – metoda

Zruší registraci objekty v zadaném modulu tak, aby k nim nelze připojit další aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*Modul*  
Ukazatel na modul.

*název_serveru*  
Kvalifikovaný název, který určuje podmnožinu objekty ovlivněné touto operací.

## <a name="return-value"></a>Návratová hodnota

Pokud je tato operace úspěšná; S_OK v opačném případě chybu HRESULT, který označuje důvod tato operace se nezdařila.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
[Module – třída](../windows/module-class.md)