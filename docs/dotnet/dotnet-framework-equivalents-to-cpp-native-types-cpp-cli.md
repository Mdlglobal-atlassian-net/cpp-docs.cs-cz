---
title: "Rozhraní .NET framework – ekvivalenty k nativním typům C++ (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: .NET Framework [C++], C++ equivalents
ms.assetid: 7f116a9a-26cd-46db-9877-a63ffdc88723
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97d12adb89baddfbfdc25e6b758a3f659e6973d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="net-framework-equivalents-to-c-native-types-ccli"></a>.NET Framework – Ekvivalenty k nativním typům C++ (C++/CLI)
V následující tabulce jsou uvedeny klíčová slova pro vestavěné typy Visual C++, které jsou aliasy předdefinovaných typů v **systému** oboru názvů.  
  
|Typ Visual C++|Typ rozhraní .NET Framework|  
|-----------------------|-------------------------|  
|**BOOL**|**System.Boolean**|  
|**podepsané char** (viz [/J](../build/reference/j-default-char-type-is-unsigned.md) informace)|**System.SByte**|  
|**unsigned char**|**System.Byte**|  
|**wchar_t**|**System.Char**|  
|**dvojité** a **long double**|**System.Double**|  
|**plovoucí desetinná čárka**|**System.Single**|  
|**int**, **podepsané int**, **dlouho**, a **podepsané dlouho**|**System.Int32**|  
|**nepodepsané int** a **dlouho bez znaménka**|**System.UInt32**|  
|**__int64** a **podepsané __int64**|**System.Int64**|  
|**__int64 bez znaménka**|**System.UInt64**|  
|**krátký** a **prostě podepsané**|**System.Int16**|  
|**short bez znaménka**|**System.UInt16**|  
|**void**|**System.Void**|  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CLI)](../dotnet/managed-types-cpp-cli.md)