---
title: "Zadejte přístup ke knihovně | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbc5ceabe60d7ee15d85495bb1a431955a589849
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-library-access"></a>Přístup ke knihovně typů
Knihovny typů vystavit rozhraní OLE ovládacího prvku pro jiné aplikace využívající technologii OLE. Pokud jeden nebo více rozhraní mají být exponovány, musí mít každý ovládací prvek OLE knihovny typů.  
  
 Následující makra povolit ovládacího prvku OLE poskytnout přístup k vlastní knihovny typů:  
  
### <a name="type-library-access"></a>Přístup ke knihovně typů  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB –](#declare_oletypelib)|Deklaruje `GetTypeLib` členské funkce ovládacího prvku OLE (musí používat v deklaraci třídy).|  
|[IMPLEMENT_OLETYPELIB –](#implement_oletypelib)|Implementuje `GetTypeLib` členské funkce ovládacího prvku OLE (musí používat v implementaci třídy).|  
  
##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB –  
 Deklaruje `GetTypeLib` funkce člena třídy ovládacího prvku.  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládací prvek související s knihovny typů.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra v řídicím souboru hlavičky – třída.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB –  
 Implementuje ovládacího prvku `GetTypeLib` – členská funkce.  
  
```   
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládací prvek související s knihovny typů.  
  
 *tlid*  
 Číslo ID knihovny typů.  
  
 `wVerMajor`  
 Typ knihovny hlavní číslo verze.  
  
 `wVerMinor`  
 Číslo podverze typu knihovny.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro musí být v souboru implementace pro ovládací prvek třídy, které používá `DECLARE_OLETYPELIB` makro.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
   
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
