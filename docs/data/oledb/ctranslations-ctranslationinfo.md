---
title: CTranslations, CTranslationInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 95bcede95c8d5de4f2c0e529a16e06277ac3240d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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