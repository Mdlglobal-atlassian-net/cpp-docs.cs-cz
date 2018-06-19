---
title: Závažná chyba C1853 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa6a67c13f76b0bf43159b9e9de95068102a2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229206"
---
# <a name="fatal-error-c1853"></a>Závažná chyba C1853
  
> '*filename*' předkompilovaný hlavičkový soubor je z předchozí verze kompilátoru, nebo předkompilovaných hlaviček C++ a používáte je z jazyka C (nebo naopak)  
  
Možné příčiny:  
  
-   Předkompilované hlavičky bylo kompilováno s předchozí verze kompilátoru. Vyzkoušejte si nutnosti rekompilace záhlaví s aktuální kompilátoru.  
  
-   Předkompilované hlavičky je C++ a používáte z C. Zkuste nutnosti rekompilace hlavičku pro použití s C zadáním jedné z [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) – možnosti kompilátoru nebo změna příponě zdrojového souboru na "c". Další informace najdete v tématu [dvě možnosti pro předkompilaci kódu](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).