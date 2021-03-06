# List of operations by function

The following tables list API operations available for use in KMS. For more information, see OpenAPI Explorer.

Alibaba Cloud also provides a command line tool for you to learn APIs and for the purpose of command line automation. For more information about how to install and use the command line tool, see [Alibaba Cloud CLI](https://www.alibabacloud.com/help/doc-detail/66653.htm).

## Key API operations

-   **CMK management**

    CMK management API operations are used to create and modify CMKs and manage their lifecycle.

    |Operation|Description|
    |:--------|:----------|
    |[CreateKey](/intl.en-US/API Reference/Key/CreateKey.md)|Creates a CMK. You can use key material created in KMS or import external key material to the CMK. Importing external key material is known as Bring Your Own Key \(BYOK\). Calling CreateKey is the first step of BYOK.|
    |[GetParametersForImport](/intl.en-US/API Reference/Key/GetParametersForImport.md)|Obtains key material to be imported. This operation is the second step of BYOK.|
    |[ImportKeyMaterial](/intl.en-US/API Reference/Key/ImportKeyMaterial.md)|Imports key material to a CMK. This operation is the final step of BYOK.|
    |[EnableKey](/intl.en-US/API Reference/Key/EnableKey.md)|Changes the state of a CMK to Enabled.|
    |[DisableKey](/intl.en-US/API Reference/Key/DisableKey.md)|Changes the state of a CMK to Disabled.|
    |[ScheduleKeyDeletion](/intl.en-US/API Reference/Key/ScheduleKeyDeletion.md)|Schedules the deletion of a CMK. After you call this operation, the CMK enters the Pending Deletion state. The CMK is automatically deleted after the specified waiting period elapses.|
    |[CancelKeyDeletion](/intl.en-US/API Reference/Key/CancelKeyDeletion.md)|Cancels the scheduled deletion of a CMK. You can cancel the scheduled deletion of a CMK before the scheduled waiting period elapses. After the deletion is canceled, the CMK enters the Enabled state again.|
    |[DeleteKeyMaterial](/intl.en-US/API Reference/Key/DeleteKeyMaterial.md)|Deletes key material of a CMK. You can directly delete key material that is imported from an external source. After key material of a CMK is deleted, the CMK enters the Pending Import state.|
    |[DescribeKey](/intl.en-US/API Reference/Key/DescribeKey.md)|Queries the detailed information of a CMK.|
    |[ListKeys](/intl.en-US/API Reference/Key/ListKeys.md)|Lists all CMKs of the current Alibaba Cloud account in the current region.|
    |[UpdateKeyDescription](/intl.en-US/API Reference/Key/UpdateKeyDescription.md)|Updates the description of a CMK.|

-   **Key version management**

    Key version management API operations are used for CMK rotation.

    |Operation|Description|
    |---------|-----------|
    |[DescribeKeyVersion](/intl.en-US/API Reference/Key/DescribeKeyVersion.md)|Queries the detailed information of a key version.|
    |[ListKeyVersions](/intl.en-US/API Reference/Key/ListKeyVersions.md)|Queries all key versions of a CMK.|
    |[UpdateRotationPolicy](/intl.en-US/API Reference/Key/UpdateRotationPolicy.md)|Updates the rotation policy of a symmetric CMK. If automatic rotation is configured, KMS automatically generates a new key version on a periodic basis.|
    |[CreateKeyVersion](/intl.en-US/API Reference/Key/CreateKeyVersion.md)|Creates a new version for a CMK. This operation is available only for asymmetric CMKs.|

-   **Cryptographic operation**

    Cryptographic API operations are used to perform cryptographic operations such as data encryption and decryption.

    |Operation|Description|
    |:--------|:----------|
    |[Encrypt](/intl.en-US/API Reference/Key/Encrypt.md)|Uses a specified CMK to encrypt data. This operation is used to encrypt data of no more than 6 KB.|
    |[GenerateDataKey](/intl.en-US/API Reference/Key/GenerateDataKey.md)|Generates a random number and encrypts the random number with a specified CMK. The ciphertext and plaintext of the random number are returned. The random number can be used as a data key to encrypt or decrypt a large amount of local data.|
    |[GenerateDataKeyWithoutPlaintext](/intl.en-US/API Reference/Key/GenerateDataKeyWithoutPlaintext.md)|Generates a random number and encrypts the random number with a specified CMK. The ciphertext of the random number is returned. The random number can be used as a data key to encrypt or decrypt a large amount of local data.|
    |[ExportDataKey](/intl.en-US/API Reference/Key/ExportDataKey.md)|Encrypts a data key by using a specific public key and exports the data key.|
    |[GenerateAndExportDataKey](/intl.en-US/API Reference/Key/GenerateAndExportDataKey.md)|Generates a random data key, encrypts the data key by using a specific CMK and public key, and returns the ciphertext encrypted by using the CMK and that encrypted by using the public key.|
    |[Decrypt](/intl.en-US/API Reference/Key/Decrypt.md)|Decrypts the ciphertext that is generated by calling the Encrypt or GenerateDataKey operation. You do not need to specify a CMK for decryption.|
    |[ReEncrypt](/intl.en-US/API Reference/Key/ReEncrypt.md)|Re-encrypts ciphertext. Decrypts the specified ciphertext, uses a different CMK to encrypt the obtained plaintext data or data key, and returns ciphertext.|
    |[AsymmetricSign](/intl.en-US/API Reference/Key/AsymmetricSign.md)|Uses the private key of an asymmetric key pair to generate a digital signature.|
    |[AsymmetricVerify](/intl.en-US/API Reference/Key/AsymmetricVerify.md)|Uses the public key of an asymmetric key pair to verify a digital signature that is generated by using the private key.|
    |[AsymmetricDecrypt](/intl.en-US/API Reference/Key/AsymmetricDecrypt.md)|Uses the private key of an asymmetric key pair to decrypt the data that is encrypted by using the public key.|
    |[AsymmetricEncrypt](/intl.en-US/API Reference/Key/AsymmetricEncrypt.md)|Uses the public key of an asymmetric key pair to encrypt data.|
    |[GetPublicKey](/intl.en-US/API Reference/Key/GetPublicKey.md)|Obtains the public key of an asymmetric key pair. You can use the public key to encrypt data or verify digital signatures offline.|

-   **Alias management**

    An alias is an independent object in KMS. It must be bound to a unique CMK. You can set the KeyId parameter in certain API operations to an alias to specify a CMK.

    |Operation|Description|
    |:--------|:----------|
    |[t22697.md\#](/intl.en-US/API Reference/Key/CreateAlias.md)|Creates an alias and binds it to a CMK.|
    |[UpdateAlias](/intl.en-US/API Reference/Key/UpdateAlias.md)|Binds an alias to a different CMK.|
    |[DeleteAlias](/intl.en-US/API Reference/Key/DeleteAlias.md)|Deletes an alias.|
    |[ListAliases](/intl.en-US/API Reference/Key/ListAliases.md)|Lists all aliases under the current Alibaba Cloud account in the current region.|
    |[ListAliasesByKeyId](/intl.en-US/API Reference/Key/ListAliasesByKeyId.md)|Lists all aliases bound to a specified CMK.|


## Secrets Manager API operations

KMS Secrets Manager hosts, protects, distributes, and rotates secrets.

|Operation|Description|
|---------|-----------|
|[CreateSecret](/intl.en-US/API Reference/Secrets/CreateSecret.md)|Creates a secret and stores the secret value in the initial version.|
|[ListSecrets](/intl.en-US/API Reference/Secrets/ListSecrets.md)|Queries all secrets created by your Alibaba Cloud account in the current region.|
|[DeleteSecret](/intl.en-US/API Reference/Secrets/DeleteSecret.md)|Deletes a secret.|
|[DescribeSecret](/intl.en-US/API Reference/Secrets/DescribeSecret.md)|Obtains the metadata of a secret.|
|[GetSecretValue](/intl.en-US/API Reference/Secrets/GetSecretValue.md)|Obtains a secret value.|
|[PutSecretValue](/intl.en-US/API Reference/Secrets/PutSecretValue.md)|Stores the secret value of a new version into a secret object.|
|[UpdateSecret](/intl.en-US/API Reference/Secrets/UpdateSecret.md)|Updates the metadata of a secret.|
|[UpdateSecretVersionStage](/intl.en-US/API Reference/Secrets/UpdateSecretVersionStage.md)|Updates the stage label that marks a secret version.|
|[RestoreSecret](/intl.en-US/API Reference/Secrets/RestoreSecret.md)|Restores a deleted secret.|
|[ListSecretVersionIds](/intl.en-US/API Reference/Secrets/ListSecretVersionIds.md)|Queries all versions of a secret.|
|[GetRandomPassword](/intl.en-US/API Reference/Secrets/GetRandomPassword.md)|Obtains a random password string.|

## Tag management API operations

CMKs support tags. You can add multiple tags to a CMK. Each tag is defined by a pair of TagKey and TagValue.

|Operation|Description|
|:--------|:----------|
|[TagResource](/intl.en-US/API Reference/Tag/TagResource.md)|Adds tags to or modifies existing tags of a CMK or secret.|
|[UntagResource](/intl.en-US/API Reference/Tag/UntagResource.md)|Removes a tag from a CMK or secret.|
|[ListResourceTags](/intl.en-US/API Reference/Tag/ListResourceTags.md)|Lists all tags of a CMK or secret.|

## Other API operations

|Operation|Description|
|:--------|:----------|
|[DescribeRegions](/intl.en-US/API Reference/Key/DescribeRegions.md)|Queries available regions under your Alibaba Cloud account.|

