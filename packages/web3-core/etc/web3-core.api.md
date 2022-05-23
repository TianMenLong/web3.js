## API Report File for "web3-core"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
/// <reference types="node" />

import { BlockNumberOrTag } from 'web3-utils';
import { BlockOutput } from 'web3-common';
import { EthExecutionAPI } from 'web3-common';
import { HexString } from 'web3-utils';
import { JsonRpcBatchRequest } from 'web3-common';
import { JsonRpcBatchResponse } from 'web3-common';
import { JsonRpcPayload } from 'web3-common';
import { JsonRpcResponse } from 'web3-common';
import { JsonRpcResult } from 'web3-common';
import { Numbers } from 'web3-utils';
import { Socket } from 'net';
import { Web3AccountProvider } from 'web3-common';
import { Web3APIMethod } from 'web3-common';
import { Web3APIParams } from 'web3-common';
import { Web3APIRequest } from 'web3-common';
import { Web3APIReturnType } from 'web3-common';
import { Web3APISpec } from 'web3-common';
import { Web3BaseProvider } from 'web3-common';
import { Web3BaseWallet } from 'web3-common';
import { Web3BaseWalletAccount } from 'web3-common';
import { Web3EventEmitter } from 'web3-common';
import { Web3EventMap } from 'web3-common';

// @public (undocumented)
export const isLegacyRequestProvider: <API extends Web3APISpec>(
	provider: SupportedProviders<API>,
) => provider is LegacyRequestProvider;

// @public (undocumented)
export const isLegacySendAsyncProvider: <API extends Web3APISpec>(
	provider: SupportedProviders<API>,
) => provider is LegacySendAsyncProvider;

// @public (undocumented)
export const isLegacySendProvider: <API extends Web3APISpec>(
	provider: SupportedProviders<API>,
) => provider is LegacySendProvider;

// @public (undocumented)
export const isSupportedProvider: <API extends Web3APISpec>(
	provider: SupportedProviders<API>,
) => boolean;

// @public (undocumented)
export const isSupportSubscriptions: <API extends Web3APISpec>(
	provider: SupportedProviders<API>,
) => boolean;

// @public (undocumented)
export const isWeb3Provider: <API extends Web3APISpec>(
	provider: SupportedProviders<API>,
) => provider is Web3BaseProvider<API>;

// @public (undocumented)
export type LegacyRequestProvider = {
	request: <R = JsonRpcResult, P = unknown>(
		payload: JsonRpcPayload<P>,
		cb: (err: Error | null, response: JsonRpcResponse<R>) => void,
	) => void;
};

// @public (undocumented)
export type LegacySendAsyncProvider = {
	sendAsync: <R = JsonRpcResult, P = unknown>(
		payload: JsonRpcPayload<P>,
	) => Promise<JsonRpcResponse<R>>;
};

// @public (undocumented)
export type LegacySendProvider = {
	send: <R = JsonRpcResult, P = unknown>(
		payload: JsonRpcPayload<P>,
		cb: (err: Error | null, response: JsonRpcResponse<R>) => void,
	) => void;
};

// @public (undocumented)
export type SupportedProviders<API extends Web3APISpec> =
	| Web3BaseProvider<API>
	| LegacyRequestProvider
	| LegacySendProvider
	| LegacySendAsyncProvider
	| string;

// @public (undocumented)
export type TransactionBuilder<API extends Web3APISpec = any> = <
	ReturnType = Record<string, unknown>,
>(options: {
	transaction: Record<string, unknown>;
	web3Context: Web3Context<API>;
	privateKey?: HexString | Buffer;
}) => Promise<ReturnType>;

// @public (undocumented)
export type TransactionTypeParser = (transaction: Record<string, unknown>) => HexString | undefined;

// @public (undocumented)
export type Web3BaseProviderConstructor = new <API extends Web3APISpec>(
	url: string,
	net?: Socket,
) => Web3BaseProvider<API>;

// @public (undocumented)
export abstract class Web3Config
	extends Web3EventEmitter<{
		[Web3ConfigEvent.CONFIG_CHANGE]: ConfigEvent<Web3ConfigOptions>;
	}>
	implements Web3ConfigOptions
{
	constructor(options?: Partial<Web3ConfigOptions>);
	// (undocumented)
	get blockHeaderTimeout(): number;
	set blockHeaderTimeout(val: number);
	// (undocumented)
	get defaultAccount(): string | null;
	set defaultAccount(val: string | null);
	// (undocumented)
	get defaultBlock(): BlockNumberOrTag;
	set defaultBlock(val: BlockNumberOrTag);
	// (undocumented)
	get defaultChain(): string;
	set defaultChain(val: string);
	// (undocumented)
	get defaultCommon(): Record<string, unknown> | null;
	set defaultCommon(val: Record<string, unknown> | null);
	// (undocumented)
	get defaultHardfork(): string;
	set defaultHardfork(val: string);
	// (undocumented)
	get defaultMaxPriorityFeePerGas(): Numbers;
	set defaultMaxPriorityFeePerGas(val: Numbers);
	// (undocumented)
	get defaultNetworkId(): Numbers | null;
	set defaultNetworkId(val: Numbers | null);
	// (undocumented)
	get defaultTransactionType(): Numbers;
	set defaultTransactionType(val: Numbers);
	// (undocumented)
	getConfig(): Web3ConfigOptions;
	// (undocumented)
	get handleRevert(): boolean;
	set handleRevert(val: boolean);
	// (undocumented)
	get maxListenersWarningThreshold(): number;
	set maxListenersWarningThreshold(val: number);
	// (undocumented)
	setConfig(options: Partial<Web3ConfigOptions>): void;
	// (undocumented)
	get transactionBlockTimeout(): number;
	set transactionBlockTimeout(val: number);
	// (undocumented)
	get transactionBuilder(): TransactionBuilder<any> | undefined;
	set transactionBuilder(val: TransactionBuilder<any> | undefined);
	// (undocumented)
	get transactionConfirmationBlocks(): number;
	set transactionConfirmationBlocks(val: number);
	// (undocumented)
	get transactionConfirmationPollingInterval(): number | null;
	set transactionConfirmationPollingInterval(val: number | null);
	// (undocumented)
	get transactionPollingInterval(): number;
	set transactionPollingInterval(val: number);
	// (undocumented)
	get transactionPollingTimeout(): number;
	set transactionPollingTimeout(val: number);
	// (undocumented)
	get transactionReceiptPollingInterval(): number | null;
	set transactionReceiptPollingInterval(val: number | null);
	// (undocumented)
	get transactionTypeParser(): TransactionTypeParser | undefined;
	set transactionTypeParser(val: TransactionTypeParser | undefined);
}

// @public (undocumented)
export enum Web3ConfigEvent {
	// (undocumented)
	CONFIG_CHANGE = 'CONFIG_CHANGE',
}

// @public (undocumented)
export interface Web3ConfigOptions {
	// (undocumented)
	blockHeaderTimeout: number;
	// (undocumented)
	defaultAccount: HexString | null;
	// (undocumented)
	defaultBlock: BlockNumberOrTag;
	// (undocumented)
	defaultChain: string;
	// (undocumented)
	defaultCommon: Record<string, unknown> | null;
	// (undocumented)
	defaultHardfork: string;
	// (undocumented)
	defaultMaxPriorityFeePerGas: Numbers;
	// (undocumented)
	defaultNetworkId: Numbers | null;
	// (undocumented)
	defaultTransactionType: Numbers;
	// (undocumented)
	handleRevert: boolean;
	// (undocumented)
	maxListenersWarningThreshold: number;
	// (undocumented)
	transactionBlockTimeout: number;
	// (undocumented)
	transactionBuilder?: TransactionBuilder;
	// (undocumented)
	transactionConfirmationBlocks: number;
	// (undocumented)
	transactionConfirmationPollingInterval: number | null;
	// (undocumented)
	transactionPollingInterval: number;
	// (undocumented)
	transactionPollingTimeout: number;
	// (undocumented)
	transactionReceiptPollingInterval: number | null;
	// (undocumented)
	transactionTypeParser?: TransactionTypeParser;
}

// @public (undocumented)
export class Web3Context<
	API extends Web3APISpec,
	RegisteredSubs extends {
		[key: string]: Web3SubscriptionConstructor<API>;
	} = any,
> extends Web3Config {
	constructor(
		providerOrContext: SupportedProviders<API> | Web3ContextInitOptions<API, RegisteredSubs>,
	);
	// (undocumented)
	get accountProvider(): Web3AccountProvider<Web3BaseWalletAccount> | undefined;
	// (undocumented)
	get currentProvider(): SupportedProviders<API>;
	set currentProvider(provider: SupportedProviders<API>);
	// (undocumented)
	static fromContextObject<T extends Web3Context<any>, T3 extends unknown[]>(
		this: Web3ContextConstructor<T, T3>,
		...args: [Web3ContextObject, ...T3]
	): T;
	// (undocumented)
	getContextObject(): Web3ContextObject<API, RegisteredSubs>;
	// (undocumented)
	static givenProvider?: SupportedProviders<never>;
	// (undocumented)
	link<T extends Web3Context<API, RegisteredSubs>>(parentContext: T): void;
	// (undocumented)
	get provider(): SupportedProviders<API>;
	set provider(provider: SupportedProviders<API>);
	// (undocumented)
	static readonly providers: {
		HttpProvider: Web3BaseProviderConstructor;
		WebsocketProvider: Web3BaseProviderConstructor;
		IpcProvider: Web3BaseProviderConstructor;
	};
	// (undocumented)
	readonly providers: {
		HttpProvider: Web3BaseProviderConstructor;
		WebsocketProvider: Web3BaseProviderConstructor;
		IpcProvider: Web3BaseProviderConstructor;
	};
	// (undocumented)
	get requestManager(): Web3RequestManager<API>;
	// (undocumented)
	get subscriptionManager(): Web3SubscriptionManager<API, RegisteredSubs> | undefined;
	// (undocumented)
	use<T extends Web3Context<any>, T2 extends unknown[]>(
		ContextRef: Web3ContextConstructor<T, T2>,
		...args: [...T2]
	): T;
	// (undocumented)
	get wallet(): Web3BaseWallet<Web3BaseWalletAccount> | undefined;
}

// @public (undocumented)
export type Web3ContextConstructor<T extends Web3Context<any>, T2 extends unknown[]> = new (
	...args: [...extras: T2, context: Web3ContextObject]
) => T;

// @public (undocumented)
export type Web3ContextFactory<
	T extends Web3Context<any>,
	T2 extends unknown[],
> = Web3ContextConstructor<T, T2> & {
	fromContextObject(this: Web3ContextConstructor<T, T2>, contextObject: Web3ContextObject): T;
};

// @public (undocumented)
export type Web3ContextInitOptions<
	API extends Web3APISpec = any,
	RegisteredSubs extends {
		[key: string]: Web3SubscriptionConstructor<API>;
	} = any,
> = {
	config?: Partial<Web3ConfigOptions>;
	provider: SupportedProviders<API>;
	requestManager?: Web3RequestManager<API>;
	subscriptionManager?: Web3SubscriptionManager<API, RegisteredSubs> | undefined;
	registeredSubscriptions?: RegisteredSubs;
	accountProvider?: Web3AccountProvider<Web3BaseWalletAccount>;
	wallet?: Web3BaseWallet<Web3BaseWalletAccount>;
};

// @public (undocumented)
export type Web3ContextObject<
	API extends Web3APISpec = any,
	RegisteredSubs extends {
		[key: string]: Web3SubscriptionConstructor<API>;
	} = any,
> = {
	config: Web3ConfigOptions;
	provider: SupportedProviders<API>;
	requestManager: Web3RequestManager<API>;
	subscriptionManager?: Web3SubscriptionManager<API, RegisteredSubs> | undefined;
	registeredSubscriptions?: RegisteredSubs;
	providers: typeof Web3RequestManager.providers;
	accountProvider?: Web3AccountProvider<Web3BaseWalletAccount>;
	wallet?: Web3BaseWallet<Web3BaseWalletAccount>;
};

// @public (undocumented)
export class Web3RequestManager<
	API extends Web3APISpec = EthExecutionAPI,
> extends Web3EventEmitter<{
	[key in Web3RequestManagerEvent]: SupportedProviders<API>;
}> {
	constructor(provider?: SupportedProviders<API>, net?: Socket);
	// (undocumented)
	get provider(): SupportedProviders<API>;
	// (undocumented)
	static get providers(): {
		HttpProvider: Web3BaseProviderConstructor;
		WebsocketProvider: Web3BaseProviderConstructor;
		IpcProvider: Web3BaseProviderConstructor;
	};
	// (undocumented)
	get providers(): {
		HttpProvider: Web3BaseProviderConstructor;
		WebsocketProvider: Web3BaseProviderConstructor;
		IpcProvider: Web3BaseProviderConstructor;
	};
	// (undocumented)
	send<Method extends Web3APIMethod<API>, ResponseType = Web3APIReturnType<API, Method>>(
		request: Web3APIRequest<API, Method>,
	): Promise<ResponseType>;
	// (undocumented)
	sendBatch(request: JsonRpcBatchRequest): Promise<JsonRpcBatchResponse<unknown>>;
	// (undocumented)
	setProvider(provider: SupportedProviders<API>, net?: Socket): void;
}

// @public (undocumented)
export enum Web3RequestManagerEvent {
	// (undocumented)
	BEFORE_PROVIDER_CHANGE = 'BEFORE_PROVIDER_CHANGE',
	// (undocumented)
	PROVIDER_CHANGED = 'PROVIDER_CHANGED',
}

// @public (undocumented)
export abstract class Web3Subscription<
	EventMap extends Web3EventMap,
	ArgsType = any,
	API extends Web3APISpec = EthExecutionAPI,
> extends Web3EventEmitter<EventMap> {
	constructor(
		args: ArgsType,
		options: {
			requestManager: Web3RequestManager<API>;
		},
	);
	// (undocumented)
	readonly args: ArgsType;
	// (undocumented)
	protected _buildSubscriptionParams(): Web3APIParams<API, 'eth_subscribe'>;
	// (undocumented)
	get id(): string | undefined;
	// (undocumented)
	get lastBlock(): BlockOutput | undefined;
	// (undocumented)
	protected _processSubscriptionError(_err: Error): void;
	// (undocumented)
	protected _processSubscriptionResult(_data: unknown): void;
	// (undocumented)
	resubscribe(): Promise<void>;
	// (undocumented)
	subscribe(): Promise<void>;
	// (undocumented)
	unsubscribe(): Promise<void>;
}

// @public (undocumented)
export type Web3SubscriptionConstructor<
	API extends Web3APISpec,
	SubscriptionType extends Web3Subscription<any, any, API> = Web3Subscription<any, any, API>,
> = new (
	args: any,
	options: {
		requestManager: Web3RequestManager<API>;
	},
) => SubscriptionType;

// @public (undocumented)
export class Web3SubscriptionManager<
	API extends Web3APISpec,
	RegisteredSubs extends {
		[key: string]: Web3SubscriptionConstructor<API>;
	},
> {
	constructor(requestManager: Web3RequestManager<API>, registeredSubscriptions: RegisteredSubs);
	// (undocumented)
	addSubscription(sub: InstanceType<RegisteredSubs[keyof RegisteredSubs]>): Promise<void>;
	// (undocumented)
	clear(): void;
	// (undocumented)
	readonly registeredSubscriptions: RegisteredSubs;
	// (undocumented)
	removeSubscription(sub: InstanceType<RegisteredSubs[keyof RegisteredSubs]>): Promise<void>;
	// (undocumented)
	readonly requestManager: Web3RequestManager<API>;
	// (undocumented)
	subscribe<T extends keyof RegisteredSubs>(
		name: T,
		args?: ConstructorParameters<RegisteredSubs[T]>[0],
	): Promise<InstanceType<RegisteredSubs[T]>>;
	// (undocumented)
	get subscriptions(): Map<string, InstanceType<RegisteredSubs[keyof RegisteredSubs]>>;
	// (undocumented)
	supportsSubscriptions(): boolean;
	// Warning: (ae-forgotten-export) The symbol "ShouldUnsubscribeCondition" needs to be exported by the entry point index.d.ts
	//
	// (undocumented)
	unsubscribe(condition?: ShouldUnsubscribeCondition): Promise<void[]>;
}

// Warnings were encountered during analysis:
//
// src/web3_config.ts:56:29 - (ae-forgotten-export) The symbol "ConfigEvent" needs to be exported by the entry point index.d.ts

// (No @packageDocumentation comment for this package)
```