---
title: Rozhraní .NET framework – ekvivalenty k nativním typům C++ (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework [C++], C++ equivalents
ms.assetid: 7f116a9a-26cd-46db-9877-a63ffdc88723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: af9038015cd8211bcd66c08b5377d43cf7639668
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-framework-equivalents-to-c-native-types-ccli"></a>.NET Framework – Ekvivalenty k nativním typům C++ (C++/CLI)
V následující tabulce jsou uvedeny klíčová slova pro vestavěné typy Visual C++, které jsou aliasy předdefinovaných typů v **systému** oboru názvů.  
  
|Typ Visual C++|Typ rozhraní .NET Framework|  
|-----------------------|-------------------------|  
|**bool**|**System.Boolean**|  
|**podepsané char** (viz [/J](../build/reference/j-default-char-type-is-unsigned.md) informace)|**System.SByte**|  
|**unsigned char**|**System.Byte**|  
|**wchar_t**|**System.Char**|  
|**dvojité** a **long double**|**System.Double**|  
|**float**|**System.Single**|  
|**int**, **podepsané int**, **dlouho**, a **podepsané dlouho**|**System.Int32**|  
|**nepodepsané int** a **dlouho bez znaménka**|**System.UInt32**|  
|**__int64** a **podepsané __int64**|**System.Int64**|  
|**__int64 bez znaménka**|**System.UInt64**|  
|**krátký** a **prostě podepsané**|**System.Int16**|  
|**short bez znaménka**|**System.UInt16**|  
|**void**|**System.Void**|  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C++/CLI)](../dotnet/managed-types-cpp-cli.md)