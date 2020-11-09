---
ms.openlocfilehash: 22c9c7ddd8513d857d96ade608e4b2e4e809dc41
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829688"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="bcca5-101">Dans cet exercice, vous allez créer une nouvelle application Azure Active Directory qui sera utilisée pour fournir les autorisations déléguées pour le connecteur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bcca5-101">In this exercise, you will create a new Azure Active Directory Application which will be used to provide the delegated permissions for the custom connector.</span></span>

<span data-ttu-id="bcca5-102">Ouvrez un navigateur et accédez au [Centre d’administration Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="bcca5-102">Open a browser and navigate to [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="bcca5-103">Choisissez le lien **Azure Active Directory** dans le menu de navigation de gauche, puis choisissez l’entrée **inscriptions des applications** dans la section **gérer** du panneau **Azure Active Directory** .</span><span class="sxs-lookup"><span data-stu-id="bcca5-103">Choose the **Azure Active Directory** link in the left navigation menu, then choose the **App registrations** entry in the **Manage** section of the **Azure Active Directory** blade.</span></span>

![Capture d’écran du panneau Azure Active Directory dans le centre d’administration Azure Active Directory](./images/app-registrations.png)

<span data-ttu-id="bcca5-105">Choisissez l’élément de menu **nouvel enregistrement** en haut du panneau **inscriptions des applications** .</span><span class="sxs-lookup"><span data-stu-id="bcca5-105">Choose the **New registration** menu item at the top of the **App Registrations** blade.</span></span>

![Capture d’écran du panneau inscriptions des applications dans le centre d’administration Azure Active Directory](./images/new-registration.png)

<span data-ttu-id="bcca5-107">Entrez `MS Graph Batch App` dans le champ **nom** .</span><span class="sxs-lookup"><span data-stu-id="bcca5-107">Enter `MS Graph Batch App` in the **Name** field.</span></span> <span data-ttu-id="bcca5-108">Dans la section **types de comptes pris en charge** , sélectionnez **comptes dans n’importe quel annuaire d’organisation**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-108">In the **Supported account types** section, select **Accounts in any organizational directory**.</span></span> <span data-ttu-id="bcca5-109">Laissez la section **URI de redirection** vide, puis choisissez **inscrire**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-109">Leave the **Redirect URI** section blank and choose **Register**.</span></span>

![Capture d’écran du Registre enregistrer une application dans le centre d’administration Azure Active Directory](./images/register-an-app.png)

<span data-ttu-id="bcca5-111">Sur le panneau de l’application de **lot MS Graph** , copiez l' **ID d’application (client)**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-111">On the **MS Graph Batch App** blade, copy the **Application (client) ID**.</span></span> <span data-ttu-id="bcca5-112">Vous en aurez besoin dans l’exercice suivant.</span><span class="sxs-lookup"><span data-stu-id="bcca5-112">You'll need this in the next exercise.</span></span>

![Capture d’écran de la page d’application inscrite](./images/app-id.png)

<span data-ttu-id="bcca5-114">Choisissez l’entrée des autorisations de l' **API** dans la section **gérer** du panneau d' **application de commandes MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="bcca5-114">Choose the **API permissions** entry in the **Manage** section of the **MS Graph Batch App** blade.</span></span> <span data-ttu-id="bcca5-115">Sélectionnez **Ajouter une autorisation** sous **autorisations d’API**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-115">Choose **Add a permission** under **API permissions**.</span></span>

![Capture d’écran du panneau autorisations d’API](./images/api-permissions.png)

<span data-ttu-id="bcca5-117">Dans le panneau **autorisations d’API de demande** , sélectionnez **Microsoft Graph** , puis **autorisations déléguées**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-117">In the **Request API permissions** blade, choose the **Microsoft Graph** , then choose **Delegated permissions**.</span></span> <span data-ttu-id="bcca5-118">Recherchez `group` , puis sélectionnez l’autorisation de **lecture et d’écriture de tous les groupes** .</span><span class="sxs-lookup"><span data-stu-id="bcca5-118">Search for `group`, then select the **Read and write all groups** delegated permission.</span></span> <span data-ttu-id="bcca5-119">Sélectionnez **Ajouter des autorisations** au bas du panneau.</span><span class="sxs-lookup"><span data-stu-id="bcca5-119">Choose **Add permissions** at the bottom of the blade.</span></span>

 ![Capture d’écran du panneau des autorisations d’API de demande](./images/select-permissions.png)

<span data-ttu-id="bcca5-121">Choisissez l’entrée **certificats et secrets** dans la section **gérer** du panneau d' **application de commandes MS Graph** , puis choisissez **nouvelle clé secrète client**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-121">Choose the **Certificates and secrets** entry in the **Manage** section of the **MS Graph Batch App** blade, then choose **New client secret**.</span></span> <span data-ttu-id="bcca5-122">Entrez `forever` dans la **Description** et sélectionnez **jamais** sous **expire**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-122">Enter `forever` in the **Description** and select **Never** under **Expires**.</span></span> <span data-ttu-id="bcca5-123">Sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="bcca5-123">Choose **Add**.</span></span>

![Capture d’écran du panneau certificat et secrets](./images/create-client-secret.png)

<span data-ttu-id="bcca5-125">Copiez la valeur de la nouvelle clé secrète.</span><span class="sxs-lookup"><span data-stu-id="bcca5-125">Copy the value for the new secret.</span></span> <span data-ttu-id="bcca5-126">Vous en aurez besoin dans l’exercice suivant.</span><span class="sxs-lookup"><span data-stu-id="bcca5-126">You'll need this in the next exercise.</span></span>

![Capture d’écran de la nouvelle clé secrète client](./images/copy-client-secret.png)

> [!IMPORTANT]
> <span data-ttu-id="bcca5-128">Cette étape est essentielle, car le secret ne sera pas accessible une fois que vous aurez fermé cette Blade.</span><span class="sxs-lookup"><span data-stu-id="bcca5-128">This step is critical as the secret will not be accessible once you close this blade.</span></span> <span data-ttu-id="bcca5-129">Enregistrez cette clé secrète dans un éditeur de texte pour l’utiliser dans les exercices à venir.</span><span class="sxs-lookup"><span data-stu-id="bcca5-129">Save this secret to a text editor for use in upcoming exercises.</span></span>

<span data-ttu-id="bcca5-130">Pour permettre la gestion des services supplémentaires accessibles via Microsoft Graph, y compris les propriétés Teams, vous devez sélectionner des étendues supplémentaires appropriées pour activer la gestion de services spécifiques.</span><span class="sxs-lookup"><span data-stu-id="bcca5-130">To enable management of additional services accessible via the Microsoft Graph, including Teams properties, you would need to select additional, appropriate scopes to enable managing specific services.</span></span> <span data-ttu-id="bcca5-131">Par exemple, pour étendre notre solution afin de créer des blocs-notes ou des plans de planification, des compartiments et des tâches OneNote, vous devez ajouter les étendues d’autorisation requises pour les API pertinentes.</span><span class="sxs-lookup"><span data-stu-id="bcca5-131">For example, to extend our solution to enable creating OneNote Notebooks or Planner plans, buckets and tasks you would need to add the required permission scopes for the relevant APIs.</span></span>
