---
title: Platform::TypeCode – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::TypeCode
dev_langs:
- C++
helpviewer_keywords:
- Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e874b3dc479755f688128b3e6690eee89929c1c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606179"
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode – výčet
Určuje číselný kategorii, která představuje předdefinovaný typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum class TypeCode {};  
```  
  
### <a name="members"></a>Členové  
  
|Typ kódu|Popis|  
|---------------|-----------------|  
|Boolean|Typem Platform::Boolean.|  
|char16|Typ default::char16.|  
|DateTime|Typ DateTime.|  
|Desetinné číslo|Číselného typu.|  
|Double|Typ default::float64.|  
|prázdný|Typ void|  
|Int16|Typ default::int16.|  
|Int32|Typ default::int32.|  
|Int64|Typ default::int64.|  
|Int8|Typ default::int8.|  
|Objekt|Platform::Object typu.|  
|Single|Typ default::float32.|  
|String|Platform::String typu.|  
|UInt16|Typ default::uint16.|  
|UInt32|Typ default::uint32.|  
|UInt64|Typ default::uint64.|  
|UInt8|Typ default::uint8.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd