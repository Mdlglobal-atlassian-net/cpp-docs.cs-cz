---
title: Cdaorelationinfo – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a49bdfb00c3f2ceba424af7bfdfa652cacec929e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951289"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo – struktura
`CDaoRelationInfo` Struktura obsahuje informace o vztah mezi dvěma tabulkami v pole definované [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();
*// Constructor  
    CString m_strName;      // Primary  
    CString m_strTable;     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;        // Secondary *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *m_strName*  
 Jedinečné názvy objekt relace. Další informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 *m_strTable*  
 Názvy v primární tabulce v vztah.  
  
 *m_strForeignTable*  
 Názvy cizí tabulky v vztah. Cizí tabulka je tabulka použitá tak, aby obsahovala cizí klíče. Obecně platí používáte cizí tabulce k navázání nebo vynutit referenční integrity. Cizí tabulka je obvykle na straně n vztah jeden mnoho. Příklady cizí tabulky jsou tabulky, které obsahují kódy pro American stavy nebo Kanadští provincie nebo objednávek zákazníků.  
  
 *m_lAttributes*  
 Obsahuje informace o typ vztahu. Hodnota této vlastnosti může být jedno z následujících:  
  
- **dbRelationUnique** je relace 1: 1.  
  
- **dbRelationDontEnforce** relace není vynucena (žádné referenční integrity).  
  
- **dbRelationInherited** existuje relace v fixní databázi, která obsahuje dvě připojené tabulky.  
  
- **dbRelationLeft** relace je levé spojení. Levé vnější spojení zahrnuje všechny záznamy z první (levém) dvou tabulek, i když nejsou zjištěny odpovídající hodnoty pro záznamy v druhé tabulce (pravém).  
  
- **dbRelationRight** relace není pravé spojení. Pravé vnější spojení zahrnuje všechny záznamy z druhého (pravém) dvou tabulek, i když nejsou zjištěny odpovídající hodnoty pro záznamy v první tabulce (levém).  
  
- **dbRelationUpdateCascade** budou přeneseny aktualizace.  
  
- **dbRelationDeleteCascade** budou přeneseny odstranění.  
  
 *m_pFieldInfos*  
 Ukazatel na pole [cdaorelationfieldinfo –](../../mfc/reference/cdaorelationfieldinfo-structure.md) struktury. Toto pole obsahuje jeden objekt pro každé pole v vztah. *M_nFields* – datový člen poskytuje počet prvků pole.  
  
 *m_nFields*  
 Počet `CDaoRelationFieldInfo` objekty v *m_pFieldInfos* – datový člen.  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na primární a sekundární výše označuje, jak je vrácené informace [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) členské funkce ve třídě `CDaoDatabase`.  
  
 Objekty relace nejsou reprezentované pomocí třídy knihovny MFC. Místo toho, objekt DAO základní objekt MFC `CDaoDatabase` třída udržuje na kolekci objektů vztah: `CDaoDatabase` zdroje členské funkce pro přístup k některé jednotlivé položky informace o vztahu, nebo k nim mají přístup všechny najednou s `CDaoRelationInfo` objekt voláním `GetRelationInfo` členské funkce obsahující objektu databáze.  
  
 Načte informace [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) – členská funkce je uložen v `CDaoRelationInfo` struktura. `CDaoRelationInfo` také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoRelationInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [CDaoRelationFieldInfo – struktura](../../mfc/reference/cdaorelationfieldinfo-structure.md)
