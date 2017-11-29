---
title: "Cdaoparameterinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoParameterInfo
dev_langs: C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68e2eff68eb4a5ae2d7868929bca169e399a7347
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo – struktura
`CDaoParameterInfo` Struktura obsahuje informace o parametru objekt definovaný pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoParameterInfo  
{  
    CString m_strName;       // Primary  
    short m_nType;           // Primary  
    ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Objekt parametr jedinečné názvy. Další informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_nType`  
 Hodnota, která označuje typ dat parametru objektu. Seznam možných hodnot najdete v tématu `m_nType` členem [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura. Další informace naleznete v tématu "Vlastnost typu" v nápovědě rozhraní DAO.  
  
 *m_varValue*  
 Hodnota parametru, uložené v [COleVariant](../../mfc/reference/colevariant-class.md) objektu.  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na primární a sekundární výše označuje, jak je vrácené informace [getparameterinfo –](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) členské funkce ve třídě `CDaoQueryDef`.  
  
 MFC není zapouzdření rozhraní DAO parametr objekty ve třídě. Objekty základní knihovny MFC rozhraní DAO querydef `CDaoQueryDef` objekty uložit parametry do jejich parametry kolekce. Pro přístup k objektům parametr v [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objektu, volání objektu querydef `GetParameterInfo` – členská funkce pro konkrétní název parametru nebo index do kolekce parametrů. Můžete použít [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) členské funkce ve spojení s `GetParameterInfo` k procházení kolekce parametrů.  
  
 Načte informace [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) – členská funkce je uložen v `CDaoParameterInfo` struktura. Volání `GetParameterInfo` pro objekt querydef, v jehož kolekce parametrů objekt parametr uložen.  
  
> [!NOTE]
>  Pokud chcete získat nebo nastavit pouze hodnotu parametru, použijte [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) a [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) členské funkce třídy `CDaoRecordset`.  
  
 `CDaoParameterInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoParameterInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)