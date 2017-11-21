---
title: "C2856 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2856
dev_langs: C++
helpviewer_keywords: C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 69b2cdf1e7f3000ef26706c937bff33266ea087a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2856"></a>C2856 chyby kompilátoru
\#uvnitř bloku #if nemůže být hdrstop – Direktiva pragma  
  
 `hdrstop` – Direktiva pragma nemůže být umístěn uvnitř těla Podmíněná kompilace bloku.  
  
 Přesunout `#pragma hdrstop` příkaz, který má oblast, která není součástí `#if/#endif` bloku.