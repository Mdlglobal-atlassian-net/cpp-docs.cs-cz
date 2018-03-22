---
title: "VCPROFILE_PATH – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_PATH
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_PATH environment variable
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea682b70f4417ef49bfca530af5f12f21699a389
ms.sourcegitcommit: 5cd2e3e51ecc8d9fc0d889555b4bfa193ba1d6a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2018
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