---
title: 'TN054: Přímé volání rozhraní DAO při použití tříd MFC DAO'
ms.date: 09/17/2019
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
ms.openlocfilehash: cef9852f762a64579e11fe4b0d8606bfc9d36709
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095979"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: Přímé volání rozhraní DAO při použití tříd MFC DAO

> [!NOTE]
> Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. 3,6 je finální verze, která je považována za zastaralou. Vizuální C++ prostředí a Průvodci nepodporují rozhraní DAO (i když třídy rozhraní DAO jsou zahrnuty a je možné je nadále používat). Společnost Microsoft doporučuje, abyste pro nové projekty používali [šablony OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a knihovnu MFC](../data/odbc/odbc-and-mfc.md) . V údržbě stávajících aplikací byste měli používat jenom rozhraní DAO.

Při použití databázových tříd knihovny MFC DAO mohou nastat situace, kdy je nutné použít rozhraní DAO přímo. Obvykle se nejedná o případ, ale knihovna MFC poskytuje některé pomocné mechanismy, které usnadňují přímé volání rozhraní DAO při kombinování použití tříd knihovny MFC s přímými voláními rozhraní DAO. Vytvoření přímého volání rozhraní DAO do metod objektu DAO spravovaného knihovnou MFC by mělo vyžadovat pouze pár řádků kódu. Potřebujete-li vytvořit a použít objekty DAO, které nejsou *spravovány* knihovnou MFC, budete muset provést trochu více práce ve skutečně volání `Release` objektu. Tato technická Poznámka vysvětluje, kdy možná budete chtít volat rozhraní DAO přímo, k čemu vám můžou pomáhat pomocníky MFC, a jak používat rozhraní DAO OLE. Nakonec tato poznámka obsahuje několik ukázkových funkcí, které ukazují, jak volat rozhraní DAO přímo pro funkce zabezpečení rozhraní DAO.

## <a name="when-to-make-direct-dao-calls"></a>Kdy provést Přímá volání rozhraní DAO

Nejběžnější situace při vytváření přímého volání rozhraní DAO nastávají, když je potřeba aktualizovat kolekce nebo když implementujete funkce, které nejsou zabaleny pomocí knihovny MFC. Nejvýznamnější funkce, která není vystavena knihovnou MFC, je zabezpečení. Pokud chcete implementovat funkce zabezpečení, budete muset použít objekty uživatelů a skupin (y) DAO přímo. Kromě zabezpečení je v MFC dostupná jenom několik dalších funkcí DAO. Patří mezi ně klonování záznamů a funkce replikace databáze a také několik pozdních přídavků rozhraní DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Stručný přehled implementace rozhraní DAO a knihovny MFC

Balení rozhraní DAO v knihovně MFC usnadňuje používání rozhraní DAO tím, že zpracovává spoustu podrobností, takže se nemusíte starat o trochu věcí. To zahrnuje inicializaci OLE, vytváření a správu objektů DAO (zejména objektů kolekce), kontrolu chyb a poskytování silně typovaného a jednoduššího rozhraní (žádné **varianty** nebo `BSTR` argumenty). Můžete provést Přímá volání rozhraní DAO a stále využívat tyto funkce. Veškerý váš kód musí být volán `Release` pro všechny objekty vytvořené přímými voláními rozhraní DAO a *nesmí* měnit žádný ukazatel rozhraní, které může knihovna MFC spoléhat na interně. Například neměňte člen *m_pDAORecordset* otevřeného `CDaoRecordset` objektu, pokud nerozumíte *všem* vnitřním důsledky. Můžete však použít rozhraní *m_pDAORecordset* k volání DAO přímo pro získání kolekce polí. V takovém případě se člen *m_pDAORecordset* neupraví. Stačí volat `Release` objekt kolekce pole, až budete hotovi s objektem.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Popis pomocníků pro snazší volání rozhraní DAO

Pomocníkům, které jsou k dispozici pro snazší volání DAO, jsou stejné pomocníky, které se používají interně ve třídách databáze knihovny MFC DAO. Tyto pomocníky slouží ke kontrole návratových kódů při vytváření přímého volání rozhraní DAO, protokolování výstupu ladění, kontrole očekávaných chyb a v případě potřeby k vyvolání vhodných výjimek. Existují dvě základní pomocné funkce a čtyři makra, která jsou namapována na jednu z těchto dvou pomocných rutin. Nejlepším vysvětlením je jednoduše přečíst kód. Viz **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**a **DAO_TRACE** v AFXDAO. H zobrazíte makra a podívejte se na **AfxDaoCheck** a **AfxDaoTrace** v DAOCORE. CPP.

## <a name="using-the-dao-ole-interfaces"></a>Používání rozhraní DAO OLE

Rozhraní OLE pro každý objekt v hierarchii objektů DAO jsou definována v hlavičkovém souboru DBDAOINT. H, který najdete v adresáři \Program Files\Microsoft Visual Studio .NET 2003 \ VC7\include. Tato rozhraní poskytují metody, které umožňují manipulovat s celou hierarchií rozhraní DAO.

Pro mnoho metod v rozhraních DAO budete muset manipulovat `BSTR` s objektem (délka předpony, která se používá v automatizaci OLE). Objekt je obvykle zapouzdřen v rámci datového typu **variant.** `BSTR` Třída `COleVariant` knihovny MFC sama dědí z datového typu **variant** . V závislosti na tom, jestli sestavíte projekt pro ANSI nebo Unicode, budou rozhraní DAO vracet ANSI nebo `BSTR`Unicode s. Dvě makra, V_BSTR a V_BSTRT, jsou užitečné, aby bylo zajištěno, že rozhraní DAO `BSTR` získá očekávaný typ.

V_BSTR extrahuje `COleVariant`člena *bstrVal* . Toto makro se obvykle používá v případě, že potřebujete předat obsah `COleVariant` metody rozhraní DAO. Následující fragment kódu ukazuje jak deklarace, tak skutečné použití dvou metod rozhraní DAO DAOUser, které využívají makro V_BSTR:

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAO 3.6 is the final version and it is considered obsolete.User *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO 3.6 is the final version and it is considered obsolete._CHECK(pUser->get_Name(&V_BSTR (&varOldName))); DAO 3.6 is the final version and it is considered obsolete._CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

Všimněte si, `VT_BSTRT` že argument zadaný `COleVariant` v konstruktoru výše zajišťuje, že při vytváření verze ANSI `BSTR` aplikace a `COleVariant` Unicode `BSTR` pro verzi Unicode sady bude v rozhraní ANSI. vaše aplikace. To je to, co rozhraní DAO očekává.

Druhé makro, V_BSTRT, extrahuje *bstrVal* člena `COleVariant` ANSI nebo Unicode v závislosti na typu sestavení (ANSI nebo Unicode). Následující kód ukazuje, jak extrahovat `BSTR` hodnotu z a `COleVariant` do `CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

Makro V_BSTRT spolu s dalšími postupy pro otevření jiných typů uložených v `COleVariant`nástroji je znázorněno v ukázce DAOVIEW. Konkrétně tento překlad je proveden v `CCrack::strVARIANT` metodě. Tato metoda, pokud je to možné, překládá hodnotu a `COleVariant` do `CString`instance.

## <a name="simple-example-of-a-direct-call-to-dao"></a>Jednoduchý příklad přímého volání rozhraní DAO

Můžou nastat situace, kdy je potřeba aktualizovat základní objekty kolekce DAO. Obvykle by to nemělo být nutné, ale pokud je to nezbytné, jedná se o jednoduchý postup. Příkladem, kdy může být nutné aktualizovat kolekci, je při provozu ve víceuživatelském prostředí s více uživateli, kteří vytvářejí nové TableDefs. V takovém případě vaše kolekce TableDefs může být zastaralá. Chcete-li aktualizovat kolekci, stačí zavolat `Refresh` metodu konkrétního objektu kolekce a vyhledat chyby:

```cpp DAO 3.6 is the final version and it is considered obsolete._CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Všimněte si, že v současné době všechna rozhraní objektů kolekce DAO jsou nedokumentované podrobnosti o implementaci tříd databáze knihovny MFC DAO.

## <a name="using-dao-directly-for-dao-security-features"></a>Přímé použití rozhraní DAO pro funkce zabezpečení rozhraní DAO

Třídy databáze knihovny MFC rozhraní DAO nebalí funkce zabezpečení rozhraní DAO. Je nutné volat metody rozhraní DAO pro použití některých funkcí zabezpečení DAO. Následující funkce nastaví systémovou databázi a pak změní heslo uživatele. Tato funkce volá tři další funkce, které jsou následně definovány.

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

Následující čtyři příklady ukazují, jak:

- Nastavte systémovou databázi DAO (. Soubor MDW).

- Nastavte výchozího uživatele a heslo.

- Změna hesla uživatele

- Změňte heslo. Soubor MDB.

### <a name="setting-the-system-database"></a>Nastavení systémové databáze

Níže je ukázková funkce pro nastavení systémové databáze, kterou bude používat aplikace. Tato funkce musí být volána před provedením jakýchkoli dalších volání rozhraní DAO.

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

### <a name="setting-the-default-user-and-password"></a>Nastavení výchozího uživatele a hesla

K nastavení výchozího uživatele a hesla pro systémovou databázi použijte tuto funkci:

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

Chcete-li změnit heslo uživatele, použijte následující funkci:

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

Chcete-li změnit heslo. Soubor MDB, použijte následující funkci:

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
