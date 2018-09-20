---
title: 'Tn054: přímé Volání rozhraní DAO při používání tříd DAO knihovny MFC | Dokumentace Microsoftu'
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
ms.openlocfilehash: b53eaa618f06ab7644edf454e097286a3ce3cc71
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393110"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: Přímé volání rozhraní DAO při používání tříd DAO knihovny MFC

> [!NOTE]
> Prostředí Visual C++ a Průvodce nepodporuje rozhraní DAO (i když jsou součástí třídy DAO a můžete stále použít). Microsoft doporučuje, abyste použili [šablony technologie OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom v udržování existujících aplikací.

Při použití databázových tříd DAO knihovny MFC, mohou nastat situace, kdy je nutné použít rozhraní DAO přímo. Obvykle to nebude mít tento případ, ale poskytuje některé mechanismy pomocné rutiny pro usnadnění vytváření přímá rozhraní DAO volání jednoduché při kombinování použití třídy knihovny MFC s přímými voláními rozhraní DAO knihovny MFC. Provedení DAO přímé volání metod objektu spravované knihovny MFC rozhraní DAO by měl vyžadovat jenom pár řádků kódu. Pokud budete muset vytvořit a používat rozhraní DAO objekty, které jsou *není* spravuje knihovny MFC, budete muset udělat pár dalších tak, že ve skutečnosti volání `Release` objektu. Tato technická Poznámka vysvětluje, kdy můžete chtít volat rozhraní DAO přímo, co můžete dělat pomocné rutiny knihovny MFC můžete a jak pomocí rozhraní DAO OLE. Nakonec tato poznámka obsahuje některé ukázkové funkce ukazuje, jak volat rozhraní DAO přímo pro rozhraní DAO funkcí zabezpečení.

## <a name="when-to-make-direct-dao-calls"></a>Kdy se má volat rozhraní DAO s přímým přístupem

Ve většině případů pro vytvoření přímého volání rozhraní DAO dojít, když kolekce je nutné aktualizovat nebo když při implementaci funkcí, které nejsou zabalené službou knihovny MFC. Nejdůležitější funkce není vystaveno v MFC je zabezpečení. Pokud chcete implementovat funkce zabezpečení, musíte přímo pomocí objektů DAO uživatelů a skupin. Kromě zabezpečení jsou k dispozici pouze několik dalších rozhraní DAO funkce nejsou podporovány v prostředí MFC. Patří mezi ně sada záznamů klonování a databáze replikace funkce, jakož i několik pozdní dodatky do DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Stručný přehled o implementaci rozhraní DAO a MFC

Zabalení knihovny MFC rozhraní DAO značek pomocí rozhraní DAO snazší díky mnoho podrobností zpracování, takže není nutné se starat o malý věci. Jedná se o inicializaci OLE, vytváření a Správa objektů DAO (zejména objekty kolekce), chyba kontrolu a poskytnutí silného typu, jednodušší rozhraní (žádné **VARIANT** nebo `BSTR` argumenty). Můžete přímé volání rozhraní DAO a přesto využívat výhod těchto funkcí. Vše váš kód musíte udělat, je volání `Release` pro všechny objekty vytvořené s přímým přístupem DAO volá a *není* měnit žádnou ukazatelů rozhraní, které knihovny MFC může záviset na interně. Například, neprovádějte žádné změny *m_pDAORecordset* členem typu open `CDaoRecordset` objekt Pokud nerozumíte *všechny* interní následky. Ale můžete je použít *m_pDAORecordset* rozhraní pro volání rozhraní DAO přímo k získání kolekce polí. V tomto případě *m_pDAORecordset* člen nebude změněn. Stačí zavolat `Release` u objektu kolekce polí až skončíte s objektem.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Jednodušší volá popis pomocných rutin, aby rozhraní DAO

Pomocné rutiny provádět volání rozhraní DAO snadněji k dispozici jsou stejné pomocné rutiny, které se používají interně ve třídách knihovny MFC rozhraní DAO databáze. Tyto pomocné rutiny slouží ke kontrole návratové kódy přímého volání rozhraní DAO při kontrole očekávaných chyb a vyvolávání příslušné výjimky v případě potřeby protokolování výstupu ladění. Existují dva základní pomocných funkcí a čtyři makra, které se mapují na jednu z těchto dvou pomocné rutiny. Nejlepší vysvětlení je jednoduše načíst kód. Zobrazit **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**, a **DAO_TRACE** v AFXDAO. H, abyste si zobrazit makra a zobrazit **AfxDaoCheck** a **AfxDaoTrace** v DAOCORE. CPP.

## <a name="using-the-dao-ole-interfaces"></a>Pomocí rozhraní DAO OLE

Rozhraní OLE pro každý objekt v hierarchii objektů DAO jsou definována v hlavičkovém souboru DBDAOINT. H, který se nachází v adresáři \Program Files\Microsoft 2003\VC7\include sady Visual Studio .NET. Tato rozhraní poskytuje metody, které umožňují manipulovat s celou hierarchii DAO.

Pro mnoho metod v rozhraní DAO, budete muset pracovat `BSTR` objektu (délka předpony řetězce používán automatizace OLE). `BSTR` Objekt je obvykle zapouzdřen v rámci **VARIANT** datového typu. Třída knihovny MFC `COleVariant` sama dědí z **VARIANT** datového typu. V závislosti na tom, zda sestavení projektu ANSI nebo Unicode, rozhraní DAO vrátí ANSI nebo Unicode `BSTR`s. Dvě makra V_BSTR a V_BSTRT, jsou užitečné pro rozhraní DAO je ujištěním, který získá `BSTR` očekávaného typu.

Extrahuje V_BSTR *bstrVal* členem `COleVariant`. Toto makro se obvykle používá, když je potřeba předat obsah `COleVariant` na metodu rozhraní DAO. Následující fragment kódu ukazuje prohlášení a skutečnému použití pro dvě metody rozhraní DAO DAOUser, které budou využívat V_BSTR makra:

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

Všimněte si, že `VT_BSTRT` zadaného v argumentu `COleVariant` konstruktor výše se zajistí, že bude ANSI `BSTR` v `COleVariant` Pokud vytváříte ANSI verze aplikace, a Unicode `BSTR` verzi kódování Unicode vaše aplikace. To je, co se očekává DAO.

Další makro V_BSTRT, který extrahuje ANSI nebo Unicode *bstrVal* člen `COleVariant` v závislosti na typu sestavení (ANSI nebo Unicode). Následující kód ukazuje, jak extrahovat `BSTR` hodnotu `COleVariant` do `CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

Makra V_BSTRT spolu s jinými technikami, chcete-li otevřít jiné typy, které jsou uloženy v `COleVariant`, je znázorněno v ukázce DAOVIEW. Konkrétně tento převod se provádí v `CCrack::strVARIANT` metody. Tuto metodu, kde je to možné, převede hodnotu `COleVariant` instanci třídy `CString`.

## <a name="simple-example-of-a-direct-call-to-dao"></a>Jednoduchým příkladem konfliktu přímého volání rozhraní DAO

Může nastat situace, když je potřeba aktualizovat příslušné objekty kolekce rozhraní DAO. Za normálních okolností to nemělo být nutné, ale je jednoduchý postup, pokud je to nezbytné. Příkladem, kdy kolekce může být potřeba aktualizovat je při fungování v prostředí s více uživateli vytvoření nového tabledefs –. Tabledefs – kolekce může v tomto případě jsou pak zastaralá. Aktualizace kolekce, stačí zavolat `Refresh` metoda objektu určité kolekce a zkontrolujte chyby:

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Všimněte si, že aktuálně všechna rozhraní kolekce objektů DAO podrobnosti nedokumentované implementace třídy databází MFC DAO.

## <a name="using-dao-directly-for-dao-security-features"></a>Pomocí rozhraní DAO přímo pro rozhraní DAO funkcí zabezpečení

Třídy databází MFC DAO nezalamují funkcí zabezpečení DAO. Je nutné volat metody rozhraní DAO použít některé funkce zabezpečení v rozhraní DAO. Tyto funkce nastaví systémovou databázi a poté změní heslo uživatele. Tato funkce volá tři další funkce, které jsou následně definována.

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

Další čtyři příklady ukazují, jak:

- Nastavení databáze systému rozhraní DAO (. Soubor MDS).

- Nastavte výchozí uživatel a heslo.

- Změňte heslo daného uživatele.

- Změňte heslo. Soubor MDB.

### <a name="setting-the-system-database"></a>Nastavení systémové databáze

Níže je ukázka funkce pro nastavení systémová databáze, který bude používat aplikace. Tato funkce musí být volána před provedením jakékoli další volání rozhraní DAO.

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

K nastavení výchozího uživatele a heslo pro systémovou databázi, použijte následující funkce:

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

### <a name="changing-the-password-of-an-mdb-file"></a>Změna hesla pro. Soubor MDB

Chcete-li změnit heslo. MDB souboru, použijte následující funkce:

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

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
