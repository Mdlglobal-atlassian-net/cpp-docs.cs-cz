---
title: CDynamicStringAccessor::SetString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs: C++
helpviewer_keywords: SetString method
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a723cb785cb8266ff17c351f02f952a5c27062f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicstringaccessorsetstring"></a>CDynamicStringAccessor::SetString
Nastaví zadaný sloupec data jako řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetString(  
   DBORDINAL nColumn,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const CHAR* pColumnName,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const WCHAR* pColumnName,  
   BaseType* data  
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Speciální hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
 `pColumnName`  
 [v] Ukazatel na řetězec znaků, který obsahuje název sloupce.  
  
 `data`  
 [v] Ukazatel na řetězec data k zápisu na zadaný sloupec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na hodnotu řetězce, který chcete nastavit zadaný sloupec. Hodnota je typu `BaseType`, která bude `CHAR` nebo `WCHAR` podle toho, jestli `_UNICODE` je definován, nebo ne.  
  
## <a name="remarks"></a>Poznámky  
 Druhý přepsat trvá formuláře název sloupce jako řetězec ANSI a třetí přepsat trvá formuláře název sloupce jako řetězec znaků Unicode.  
  
 Pokud `_SECURE_ATL` je definována mít nenulovou hodnotu, bude generována chyba běhového modulu assertion, pokud vstupní `data` string je delší než maximální povolená délka sloupce odkazované data. Vstupní řetězec, jinak bude zkrácen, pokud je delší než maximální povolenou délku.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)