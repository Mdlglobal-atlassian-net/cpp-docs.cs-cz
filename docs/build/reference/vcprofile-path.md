---
title: "VCPROFILE_PATH – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VCPROFILE_PATH
dev_langs: C++
helpviewer_keywords: VCPROFILE_PATH environment variable
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d5b4a2bbb46e906883f3f0c99c84d3b12cc0f104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vcprofilepath"></a>VCPROFILE_PATH
Zadejte adresář, který chcete vytvořit soubory .pgc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VCPROFILE_PATH=path  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Cesta k adresáři, ve které .pgc soubory budou přidány.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení se ve stejném adresáři jako binární profilovaný vytváří soubory .pgc.  Ale pokud absolutní cesta binárního souboru neexistuje, jako při spuštění profilu scénáře na jiný počítač, ze které byla vytvořena binárního souboru může být případ, můžete nastavit `VCPROFILE_PATH` na cestu, která existuje.  
  
## <a name="example"></a>Příklad  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)