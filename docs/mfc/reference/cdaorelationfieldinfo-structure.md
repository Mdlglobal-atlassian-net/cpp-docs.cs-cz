---
title: "Cdaorelationfieldinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoRelationFieldInfo
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8b9d27154608a19da1e575a46ec424f11eec2e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo – struktura
`CDaoRelationFieldInfo` Struktura obsahuje informace o pole v vztah definovaný pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoRelationFieldInfo  
{  
    CString m_strName;           // Primary  
    CString m_strForeignName;    // Primary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Název pole ve vztahu k primární tabulce.  
  
 `m_strForeignName`  
 Název pole v tabulce cizí vztahu.  
  
## <a name="remarks"></a>Poznámky  
 Objekt DAO vztah určuje pole v primární tabulce a pole v cizí tabulky, které definují vztah. Odkazy na primární v výše uvedená definice struktury označuje, jak se vrátí informace ve `m_pFieldInfos` členem [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objekt získá voláním [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)funkce člena třídy `CDaoDatabase`.  
  
 Objekty vztah a vztah pole objekty nejsou reprezentované pomocí třídy knihovny MFC. Místo toho s objektem DAO objekty základní MFC objekty třídy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obsahovat kolekce objektů vztah názvem kolekce vztahů. Každý objekt relace, obsahuje kolekci vztah pole objektů. Každý objekt pole vztah koreluje s poli v tabulce cizí pole v primární tabulce. Dohromady, objekty pole vztah definujte skupinu polí v každé tabulce, které společně definují vztah. `CDaoDatabase`Umožňuje vám přístup k objektům vztah s `CDaoRelationInfo` objekt voláním `GetRelationInfo` – členská funkce. `CDaoRelationInfo` Objekt, pak má datový člen `m_pFieldInfos`, která odkazuje na pole `CDaoRelationFieldInfo` objekty.  
  
 Volání [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) členské funkce obsahující `CDaoDatabase` objekt v jehož vztahů kolekce je uložená relace objekt vás zajímá. Potom přístup `m_pFieldInfos` členem [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objektu. `CDaoRelationFieldInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoRelationFieldInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo – struktura](../../mfc/reference/cdaorelationinfo-structure.md)
