---
title: CDaoRelationInfo – struktura
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: 1bf60bd3f076dbf682b92898d66cc5f96841c9e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627276"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo – struktura

`CDaoRelationInfo` Struktura obsahuje informace o vztahu mezi dvěma tabulkami v definované [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
struct CDaoRelationInfo
{
    CDaoRelationInfo();                     // Constructor
    CString m_strName;                      // Primary
    CString m_strTable;                     // Primary
    CString m_strForeignTable;              // Primary
    long m_lAttributes;                     // Secondary
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Objekt vztahu jedinečné názvy. Další informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_strTable*<br/>
Názvy ve vztahu primární tabulce.

*m_strForeignTable*<br/>
Názvy tabulce cizího ve vztahu. Tabulka cizího je tabulka obsahovaly cizí klíče. Tabulka cizího se obecně používá k navázání nebo vynutit referenční integritu. Tabulka cizího je obvykle na straně n vztah jeden mnoho. Cizí tabulky příklady tabulky obsahující kódy pro amerických států nebo Kanadské provincie nebo objednávek zákazníků.

*m_lAttributes*<br/>
Obsahuje informace o typu vztahu. Hodnota této vlastnosti může být kterýkoli z následujících:

- `dbRelationUnique` Je relace 1: 1.

- `dbRelationDontEnforce` Relace není vynucena (žádná referenční integrita).

- `dbRelationInherited` Existuje relace v databázi fixní, která obsahuje dvě připojené tabulky.

- `dbRelationLeft` Relace je levé spojení. Levé vnější spojení zahrnuje všechny záznamy z první (vlevo) dvou tabulek, i když nejsou zjištěny odpovídající hodnoty pro záznamy v tabulce druhé (napravo).

- `dbRelationRight` Relace je pravé spojení. Pravé vnější spojení zahrnuje všechny záznamy z druhé (napravo) dvou tabulek, i když nejsou zjištěny odpovídající hodnoty pro záznamy v první tabulce (vlevo).

- `dbRelationUpdateCascade` Aktualizace budou přeneseny.

- `dbRelationDeleteCascade` Odstranění budou přeneseny.

*m_pFieldInfos*<br/>
Ukazatel na pole [cdaorelationfieldinfo –](../../mfc/reference/cdaorelationfieldinfo-structure.md) struktury. Pole obsahuje jeden objekt pro každé pole v vztah. `m_nFields` Datový člen vrací počet prvků pole.

*m_nFields*<br/>
Počet `CDaoRelationFieldInfo` objekty v `m_pFieldInfos` datový člen.

## <a name="remarks"></a>Poznámky

Odkazy na primární a sekundární výše určit, jak vrácené informace [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) členské funkce ve třídě `CDaoDatabase`.

Objekty relace nejsou reprezentovány třídy knihovny MFC. Místo toho, objekt DAO základní objekt knihovny MFC `CDaoDatabase` třída udržuje kolekci objektů vztah: `CDaoDatabase` poskytuje členské funkce pro přístup k některé jednotlivých položek informace o vztahu, nebo k nim přistupovat všechny najednou s `CDaoRelationInfo` objektu voláním `GetRelationInfo` členská funkce obsahující objekt databáze.

Načte informace [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) členská funkce je uložen v `CDaoRelationInfo` struktury. `CDaoRelationInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoRelationInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[CDaoRelationFieldInfo – struktura](../../mfc/reference/cdaorelationfieldinfo-structure.md)
