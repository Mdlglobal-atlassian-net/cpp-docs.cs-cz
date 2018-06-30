---
title: 'TN054: Volání rozhraní DAO přímo při používání tříd DAO knihovny MFC | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dao
dev_langs:
- C++
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f060364a8c08a32acae49a0386911486251b0e31
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122448"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: Přímé volání rozhraní DAO při používání tříd DAO knihovny MFC

> [!NOTE]
> Prostředí Visual C++ a průvodců nepodporují rozhraní DAO (i když jsou zahrnuté třídy DAO a můžete je dál používat). Microsoft doporučuje používat [šablony technologie OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom pro údržbu existujících aplikací.

Při použití databázových tříd MFC rozhraní DAO, může být situace, kdy je potřeba použít rozhraní DAO přímo. Obvykle to nebude tento případ, ale MFC poskytl některé mechanismy Pomocník usnadňuje vytváření přímá rozhraní DAO volání jednoduché při kombinování použití třídy MFC se přímá volání rozhraní DAO. Provedení přímé DAO volání metod spravované knihovny MFC rozhraní DAO objektu by měla vyžadovat jenom pár řádků kódu. Pokud budete muset vytvořit a použít rozhraní DAO objekty, které jsou *není* spravuje MFC, budete muset provést trochu další práci ve skutečnosti voláním `Release` objektu. Tato technická Poznámka vysvětluje při můžete chtít DAO volat přímo, co můžete udělat Pomocníci MFC vám pomohou a jak používat rozhraní DAO OLE. Nakonec tato poznámka poskytuje některé funkce ukázka znázorňující způsob volání rozhraní DAO přímo DAO funkce zabezpečení.

## <a name="when-to-make-direct-dao-calls"></a>Při volání přímé rozhraní DAO

Ve většině případů pro vytvoření přímého volání rozhraní DAO dojít, když je potřeba aktualizovat kolekce nebo při implementaci funkce, které nejsou zabalené službou MFC. Nejdůležitější funkce nejsou viditelné v prostředí MFC je zabezpečení. Pokud chcete implementovat funkce zabezpečení, musíte použít rozhraní DAO jiní uživatelé a skupiny objektů přímo. Kromě zabezpečení jsou k dispozici pouze několik dalších DAO funkce nepodporované MFC. Mezi ně patří sada záznamů klonování a databáze replikace funkce, jakož i několik pozdní dodatky do DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Stručný přehled implementace rozhraní DAO a knihovny MFC

Zabalení knihovny MFC rozhraní DAO značek pomocí rozhraní DAO jednodušší zpracování spousty podrobností tak nemají starosti málo věcí. To zahrnuje inicializace OLE, vytváření a Správa objektů DAO (zejména objekty kolekce), chyba kontrolu a poskytování silného typu jednodušší rozhraní (žádné **VARIANT** nebo `BSTR` argumenty). Můžete nastavit přímá volání rozhraní DAO a nadále využívat výhod těchto funkcí. Všechny musíte udělat kódu je volání `Release` pro všechny objekty vytvořené pomocí rozhraní DAO přímé volání a *není* upravovat ukazatele rozhraní, které může MFC závisí na interně. Například Neupravujte *m_pDAORecordset* členem otevřenou `CDaoRecordset` objektu, pokud nerozumíte *všechny* interní následky. Může, ale použít *m_pDAORecordset* rozhraní k volání rozhraní DAO přímo k získání kolekce pole. V takovém případě *m_pDAORecordset* člen by být upraven. Stačí zavolat `Release` na objekt kolekce pole až skončíte s daným objektem.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Volá jednodušší popis pomocné rutiny, aby rozhraní DAO

Poskytuje aby volání rozhraní DAO jednodušší pomocníky stejné pomocné rutiny, které se používá interně do tříd MFC rozhraní DAO databáze. Tyto pomocné rutiny slouží ke kontrole návratové kódy při provádění přímé volání DAO, protokolování výstupu ladění kontrola očekávané chyb a vyvolávání příslušné výjimky v případě potřeby. Existují dva základní pomocných funkcí a čtyři makra, které jsou mapovány na jednu z těchto dvou pomocné rutiny. Nejlepší vysvětlení by jednoduše načíst kód. V tématu **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**, a **DAO_TRACE** v AFXDAO. H vidět makra, a v tématu **AfxDaoCheck** a **AfxDaoTrace** v DAOCORE. CPP.

## <a name="using-the-dao-ole-interfaces"></a>Pomocí rozhraní DAO OLE

Rozhraní OLE pro každý objekt v hierarchii objekt DAO jsou definovány v záhlaví souboru DBDAOINT. H, který se nachází v adresáři \Program Files\Microsoft 2003\VC7\include sady Visual Studio .NET. Tato rozhraní poskytují metody, které umožňují pracovat s celou hierarchii DAO.

Pro mnoho metody v rozhraní DAO, budete muset upravit `BSTR` objektu (délka předpony řetězec používá v OLE – automatizace). `BSTR` Objekt se obvykle zapouzdřené v rámci **VARIANT** datového typu. Třída knihovny MFC `COleVariant` samotné dědí z **VARIANT** datového typu. V závislosti na tom, jestli sestavení projektu pro ANSI nebo Unicode, rozhraní DAO vrátí ANSI nebo Unicode `BSTR`s. Dvě makra, V_BSTR a V_BSTRT, jsou užitečné pro zabezpečit, aby rozhraní DAO získá `BSTR` očekávaného typu.

Extrahuje V_BSTR *bstrVal* členem `COleVariant`. Toto makro se obvykle používá, když potřebujete předat obsah `COleVariant` na metodu rozhraní DAO. Následující fragment kódu ukazuje, jak deklarace a skutečném použití pro rozhraní DAO DAOUser dvě metody, které využívají makro V_BSTR:

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted
DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;

DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

Všimněte si, že `VT_BSTRT` zadaného v argumentu `COleVariant` konstruktor výše zajistí, že bude ANSI `BSTR` v `COleVariant` Pokud vytvoříte na ANSI verzi vaší aplikace a Unicode `BSTR` pro verzi kódování Unicode vaše aplikace. Je to, co DAO očekává.

Další makro V_BSTRT, který extrahuje ANSI nebo Unicode *bstrVal* členem `COleVariant` v závislosti na typu sestavení (ANSI nebo Unicode). Následující kód ukazuje, jak z něho extrahovat `BSTR` z hodnoty `COleVariant` do `CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

Makro V_BSTRT, spolu s jinými technikami, chcete-li otevřít jiné typy, které jsou uložené v `COleVariant`, je znázorněn v ukázce DAOVIEW. Konkrétně tato překlad se provádí v `CCrack::strVARIANT` metoda. Tuto metodu, kde je to možné, znamená, že hodnota `COleVariant` do instance `CString`.

## <a name="simple-example-of-a-direct-call-to-dao"></a>Jednoduchý příklad přímé volání rozhraní DAO

Mohou nastat situace, když je potřeba aktualizovat základní kolekce objektů DAO. Za normálních okolností toto by nemělo být nutné, ale je jednoduchý postup v případě potřeby. Příklad při kolekce může být potřeba aktualizovat, je při fungování v prostředí s více uživateli vytvoření nového tabledefs –. V takovém případě tabledefs – kolekce, mohou být zastaralé. Aktualizace kolekce, stačí zavolat `Refresh` metoda objektu určitou kolekci a zkontrolujte chyby:

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Upozorňujeme, že aktuálně všechny rozhraní DAO pro objekt kolekce jsou nedokumentovanými implementace podrobnosti o databázové třídy MFC rozhraní DAO.

## <a name="using-dao-directly-for-dao-security-features"></a>Pomocí rozhraní DAO přímo pro funkce zabezpečení rozhraní DAO

Databázové třídy MFC rozhraní DAO není zalomen DAO funkce zabezpečení. Je třeba volat metody rozhraní DAO používat některé funkce zabezpečení DAO. Následující funkce nastaví systémové databáze a poté změní heslo uživatele. Tato funkce volá tři další funkce, které jsou následně definované.

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

    // Set system database before MFC initilizes DAO
    // NOTE: An MFC module uses only one instance
    // of a DAO database engine object. If you have
    // called a DAO object in your application prior
    // to calling the function below, you must call
    // AfxDaoTerm to destroy the existing database
    // engine object. Otherwise, the database engine
    // object already in use will be reused, and setting
    // a system datbase will have no effect.
    //
    // If you have used a DAO object prior to calling
    // this function it is important that DAO be
    // terminated with AfxDaoTerm since an MFC
    // module only gets one copy of the database engine
    // and that engine will be reused if it hasn't been
    // terminated. In other words, if you do not call
    // AfxDaoTerm and there is currently a database
    // initialized, setting the system database will
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

Další čtyři příklady ukazují postup:

- Nastavit systémové databáze rozhraní DAO (. Soubor MDS).

- Nastavte výchozí uživatel a heslo.

- Změňte heslo uživatele.

- Změnit heslo. Soubor MDB.

### <a name="setting-the-system-database"></a>Nastavení systémové databáze

Níže je ukázková funkce nastavit systémovou databázi, která se použije v aplikaci. Tato funkce musí být volána, než jsou provedeny žádné další volání rozhraní DAO.

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>Nastavení výchozího uživatele a heslo

Pokud chcete nastavit výchozí uživatel a heslo pro systémovou databázi, použijte následující funkce:

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>Změna hesla uživatele

Chcete-li změnit heslo uživatele, použijte následující funkce:

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>Změna hesla. Soubor MDB

Chcete-li změnit heslo. MDB souborů, použijte následující funkce:

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
