---
title: CTranslations, CTranslationInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szCatalog
- m_szSourceCatalog
- m_szTargetSchema
- m_szTargetCatalog
- m_szTargetName
- CTranslationInfo
- m_szSourceName
- m_szSchema
- CTranslations
- m_szName
- m_szSourceSchema
dev_langs: C++
helpviewer_keywords:
- m_szSourceSchema
- m_szSourceCatalog
- m_szSchema
- m_szTargetName
- m_szSourceName
- CTranslations typedef class
- m_szCatalog
- m_szTargetCatalog
- m_szName
- CTranslationInfo parameter class
- m_szTargetSchema
ms.assetid: 19a64828-2d4c-42a0-8bfb-b010e334a9b3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96b6602bb4bf472979ff11bb1d4df351559cc066
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctranslations-ctranslationinfo"></a>CTranslations, CTranslationInfo
Call – třída definice typedef **CTranslations** k implementaci jeho – třída parametru **CTranslationInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje znak překladů definovaném v katalogu, které jsou dostupné pro daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [PŘEKLADY řádků](https://msdn.microsoft.com/en-us/library/ms725365.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szCatalog|TRANSLATION_CATALOG|  
|m_szSchema|TRANSLATION_SCHEMA|  
|m_szName|TRANSLATION_NAME|  
|m_szSourceCatalog|SOURCE_CHARACTER_SET_CATALOG|  
|m_szSourceSchema|SOURCE_CHARACTER_SET_SCHEMA|  
|m_szSourceName|SOURCE_CHARACTER_SET_NAME|  
|m_szTargetCatalog|TARGET_CHARACTER_SET_CATALOG|  
|m_szTargetSchema|TARGET_CHARACTER_SET_SCHEMA|  
|m_szTargetName|TARGET_CHARACTER_SET_NAME|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [Ukázky CatDB](../../visual-cpp-samples.md)   
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)