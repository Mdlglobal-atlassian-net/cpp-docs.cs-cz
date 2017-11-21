---
title: "DAO modul inicializace a ukončování databázového | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.data
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4e32930b53c6e05abf692474fdb1236fe007a1eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO
Při použití knihovny MFC rozhraní DAO objekty, musí být nejprve databázový stroj DAO inicializovat a pak ukončen před aplikace nebo knihovna DLL se ukončí. Dvě funkce `AfxDaoInit` a `AfxDaoTerm`, provedení těchto úloh.  
  
### <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO  
  
|||  
|-|-|  
|[Afxdaoinit –](#afxdaoinit)|Inicializuje databázový stroj DAO.|  
|[Afxdaoterm –](#afxdaoterm)|Ukončí databázový stroj DAO.|  
  
##  <a name="afxdaoinit"></a>Afxdaoinit –  
 Tato funkce inicializuje databázový stroj DAO.  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>Poznámky  
 Ve většině případů nemusíte volání `AfxDaoInit` vzhledem k tomu, že aplikace automaticky nazve je když ho nepotřebují.  
  
 Související informace a příklad volání `AfxDaoInit`, najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="afxdaoterm"></a>Afxdaoterm –  
 Tato funkce se ukončuje databázový stroj DAO.  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>Poznámky  
 Obvykle stačí pro volání této funkce v běžný MFC DLL; aplikace se automaticky zavolá `AfxDaoTerm` Pokud je to potřeba.  
  
 V běžných knihovnách DLL MFC volání `AfxDaoTerm` před `ExitInstance` funkce, ale po všech objektů knihovny MFC rozhraní DAO zničena.  
  
 Související informace najdete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
