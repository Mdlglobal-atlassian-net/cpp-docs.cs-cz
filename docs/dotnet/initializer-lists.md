---
title: "Inicializační seznamy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99d62f1aec8cf06fff5de98f4681ddc67c3a9e71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="initializer-lists"></a>Inicializační seznamy
Inicializační seznamy v konstruktorech se nyní nazývají před konstruktor základní třídy.  
  
## <a name="remarks"></a>Poznámky  
 Před Visual C++ 2005 byla volána konstruktor základní třídy před inicializačním seznam při kompilaci s spravovaných rozšíření jazyka C++. Teď když kompilujete s **/CLR**, inicializátoru seznamu jako první.  
  
## <a name="see-also"></a>Viz také  
 [Obecné jazykové změny (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)