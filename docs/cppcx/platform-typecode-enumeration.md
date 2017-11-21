---
title: "Výčet Platform::TypeCode | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::TypeCode
dev_langs: C++
helpviewer_keywords: Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0c217824496f0cf4e69c8fba89fd614a8049a8c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode – výčet
Určuje číselnou kategorii, která představuje předdefinovaný typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum class TypeCode {};  
```  
  
### <a name="members"></a>Členové  
  
|Typ kódu|Popis|  
|---------------|-----------------|  
|Boolean|Platform::Boolean – typ.|  
|char16|Typ default::char16.|  
|DateTime|Typ DateTime.|  
|Desetinné číslo|Číselného typu.|  
|Double|Typ default::float64.|  
|prázdný|Void|  
|Int16|Typ default::int16.|  
|Int32|Typ default::int32.|  
|Int64|Typ default::int64.|  
|int8|Typ default::int8.|  
|Objekt|Typ Platform::Object.|  
|Single|Typ default::float32.|  
|String|Typ Platform::String.|  
|UInt16|Typ default::uint16.|  
|UInt32|Typ default::uint32.|  
|UInt64|Typ default::uint64.|  
|UInt8|Typ default::uint8.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd