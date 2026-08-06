## Get Internet Quality Index (IQI) summary

`client.Radar.Quality.IQI.Summary(ctx, query) (*QualityIQISummaryResponse, error)`

**get** `/radar/quality/iqi/summary`

Retrieves a summary (percentiles) of bandwidth, latency, or DNS response time from the Radar Internet Quality Index (IQI).

### Parameters

- `query QualityIQISummaryParams`

  - `Metric param.Field[QualityIQISummaryParamsMetric]`

    Defines which metric to return (bandwidth, latency, or DNS response time).

    - `const QualityIQISummaryParamsMetricBandwidth QualityIQISummaryParamsMetric = "BANDWIDTH"`

    - `const QualityIQISummaryParamsMetricDNS QualityIQISummaryParamsMetric = "DNS"`

    - `const QualityIQISummaryParamsMetricLatency QualityIQISummaryParamsMetric = "LATENCY"`

  - `ASN param.Field[[]string]`

    Filters results by Autonomous System. Specify one or more Autonomous System Numbers (ASNs) as a comma-separated list. Prefix with `-` to exclude ASNs from results. For example, `-174, 3356` excludes results from AS174, but includes results from AS3356.

  - `Continent param.Field[[]string]`

    Filters results by continent. Specify a comma-separated list of alpha-2 codes. Prefix with `-` to exclude continents from results. For example, `-EU,NA` excludes results from EU, but includes results from NA.

  - `DateEnd param.Field[[]Time]`

    End of the date range (inclusive). Alternative to `dateRange`; provide together with `dateStart`. When requesting comparison series, every series must resolve to the same duration as the main series. Each `dateStart`/`dateEnd` is floored to the nearest 15 minutes before evaluation, so windows whose durations match only before alignment may be rejected.

  - `DateRange param.Field[[]string]`

    Filters results by relative date range ending at the current time, with each value producing a separate series. Use `<n>d` for days (up to `364d`) or `<n>w` for weeks (up to `52w`). Append `control` to request the equivalent previous period for comparison: the comparison window is shifted back by the current window's length rounded up to a whole number of weeks, so it keeps the same weekday alignment and does not overlap the current window (e.g. `7dcontrol` covers days -14 to -7, `10dcontrol` covers days -24 to -14). For example, pass `7d` and `7dcontrol` to compare this week with the previous week. All series must resolve to the same duration as the main series; relative ranges (including `control`) satisfy this automatically. Use this parameter or set specific start and end dates (`dateStart` and `dateEnd` parameters).

  - `DateStart param.Field[[]Time]`

    Start of the date range. Alternative to `dateRange`; provide together with `dateEnd`. When requesting comparison series, every series must resolve to the same duration as the main series. Each `dateStart`/`dateEnd` is floored to the nearest 15 minutes before evaluation, so windows whose durations match only before alignment may be rejected.

  - `Format param.Field[QualityIQISummaryParamsFormat]`

    Format in which results will be returned.

    - `const QualityIQISummaryParamsFormatJson QualityIQISummaryParamsFormat = "JSON"`

    - `const QualityIQISummaryParamsFormatCsv QualityIQISummaryParamsFormat = "CSV"`

  - `Location param.Field[[]string]`

    Filters results by location. Specify a comma-separated list of alpha-2 codes. Prefix with `-` to exclude locations from results. For example, `-US,PT` excludes results from the US, but includes results from PT.

  - `Name param.Field[[]string]`

    Array of names used to label the series in the response.

### Returns

- `type QualityIQISummaryResponse struct{…}`

  - `Meta QualityIQISummaryResponseMeta`

    Metadata for the results.

    - `ConfidenceInfo QualityIQISummaryResponseMetaConfidenceInfo`

      - `Annotations []QualityIQISummaryResponseMetaConfidenceInfoAnnotation`

        - `DataSource QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource`

          Data source for annotations.

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceAll QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "ALL"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceAIBots QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "AI_BOTS"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceAIGateway QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "AI_GATEWAY"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceBGP QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "BGP"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceBots QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "BOTS"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceConnectionAnomaly QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "CONNECTION_ANOMALY"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceCT QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "CT"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceDNS QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "DNS"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceDNSMagnitude QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "DNS_MAGNITUDE"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceDNSAS112 QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "DNS_AS112"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceDos QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "DOS"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceEmailRouting QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "EMAIL_ROUTING"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceEmailSecurity QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "EMAIL_SECURITY"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceFw QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "FW"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceFwPg QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "FW_PG"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceHTTP QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "HTTP"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceHTTPControl QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "HTTP_CONTROL"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceHTTPCrawlerReferer QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "HTTP_CRAWLER_REFERER"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceHTTPOrigins QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "HTTP_ORIGINS"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceIQI QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "IQI"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceLeakedCredentials QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "LEAKED_CREDENTIALS"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceNet QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "NET"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceRobotsTXT QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "ROBOTS_TXT"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceSpeed QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "SPEED"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSourceWorkersAI QualityIQISummaryResponseMetaConfidenceInfoAnnotationsDataSource = "WORKERS_AI"`

        - `Description string`

        - `EndDate Time`

        - `EventType QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType`

          Event type for annotations.

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventTypeEvent QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType = "EVENT"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventTypeGeneral QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType = "GENERAL"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventTypeOutage QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType = "OUTAGE"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventTypePartialProjection QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType = "PARTIAL_PROJECTION"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventTypePipeline QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType = "PIPELINE"`

          - `const QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventTypeTrafficAnomaly QualityIQISummaryResponseMetaConfidenceInfoAnnotationsEventType = "TRAFFIC_ANOMALY"`

        - `IsInstantaneous bool`

          Whether event is a single point in time or a time range.

        - `LinkedURL string`

        - `StartDate Time`

        - `Tags []string`

      - `Level int64`

        Provides an indication of how much confidence Cloudflare has in the data.

    - `DateRange []QualityIQISummaryResponseMetaDateRange`

      - `EndTime Time`

        Adjusted end of date range.

      - `StartTime Time`

        Adjusted start of date range.

    - `LastUpdated Time`

      Timestamp of the last dataset update.

    - `Normalization QualityIQISummaryResponseMetaNormalization`

      Normalization method applied to the results. Refer to [Normalization methods](https://developers.cloudflare.com/radar/concepts/normalization/).

      - `const QualityIQISummaryResponseMetaNormalizationPercentage QualityIQISummaryResponseMetaNormalization = "PERCENTAGE"`

      - `const QualityIQISummaryResponseMetaNormalizationMin0Max QualityIQISummaryResponseMetaNormalization = "MIN0_MAX"`

      - `const QualityIQISummaryResponseMetaNormalizationMinMax QualityIQISummaryResponseMetaNormalization = "MIN_MAX"`

      - `const QualityIQISummaryResponseMetaNormalizationRawValues QualityIQISummaryResponseMetaNormalization = "RAW_VALUES"`

      - `const QualityIQISummaryResponseMetaNormalizationPercentageChange QualityIQISummaryResponseMetaNormalization = "PERCENTAGE_CHANGE"`

      - `const QualityIQISummaryResponseMetaNormalizationRollingAverage QualityIQISummaryResponseMetaNormalization = "ROLLING_AVERAGE"`

      - `const QualityIQISummaryResponseMetaNormalizationOverlappedPercentage QualityIQISummaryResponseMetaNormalization = "OVERLAPPED_PERCENTAGE"`

      - `const QualityIQISummaryResponseMetaNormalizationRatio QualityIQISummaryResponseMetaNormalization = "RATIO"`

    - `Units []QualityIQISummaryResponseMetaUnit`

      Measurement units for the results.

      - `Name string`

      - `Value string`

  - `Summary0 QualityIQISummaryResponseSummary0`

    - `P25 string`

    - `P50 string`

    - `P75 string`

### Example

```go
package main

import (
  "context"
  "fmt"

  "github.com/cloudflare/cloudflare-go"
  "github.com/cloudflare/cloudflare-go/option"
  "github.com/cloudflare/cloudflare-go/radar"
)

func main() {
  client := cloudflare.NewClient(
    option.WithAPIToken("Sn3lZJTBX6kkg7OdcBUAxOO963GEIyGQqnFTOFYY"),
  )
  response, err := client.Radar.Quality.IQI.Summary(context.TODO(), radar.QualityIQISummaryParams{
    Metric: cloudflare.F(radar.QualityIQISummaryParamsMetricBandwidth),
  })
  if err != nil {
    panic(err.Error())
  }
  fmt.Printf("%+v\n", response.Meta)
}
```

#### Response

```json
{
  "result": {
    "meta": {
      "confidenceInfo": {
        "annotations": [
          {
            "dataSource": "ALL",
            "description": "Cable cut in Tonga",
            "endDate": "2019-12-27T18:11:19.117Z",
            "eventType": "EVENT",
            "isInstantaneous": true,
            "linkedUrl": "https://example.com",
            "startDate": "2019-12-27T18:11:19.117Z",
            "tags": [
              "BOT_CLASS"
            ]
          }
        ],
        "level": 0
      },
      "dateRange": [
        {
          "endTime": "2022-09-17T10:22:57.555Z",
          "startTime": "2022-09-16T10:22:57.555Z"
        }
      ],
      "lastUpdated": "2019-12-27T18:11:19.117Z",
      "normalization": "PERCENTAGE",
      "units": [
        {
          "name": "*",
          "value": "requests"
        }
      ]
    },
    "summary_0": {
      "p25": "32.20938",
      "p50": "61.819881",
      "p75": "133.813087"
    }
  },
  "success": true
}
```
# quickstart-android
* GCX++++

```npm install ethereum-identity-kitnpm install ethereum-identity-kit wagmi viem@2.x @tanstack/react-queryimport { WagmiProvider } from 'wagmi'

* import { wagmiConfig } from '#/lib/wagmi'

* import { TransactionProvider } from 'ethereum-identity-kit'

* import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
 
const queryClient = new QueryClient()
 
## export default function App({ Component, pageProps }: AppProps) {
  return (
    <QueryClientProvider client={queryClient}>
      <WagmiProvider config={wagmiConfig}>
        <TransactionProvider>
          <Component {...pageProps} />
        </TransactionProvider>
      </WagmiProvider>
    </QueryClientProvider>
  )
}
* import { ProfileCard } from 'ethereum-identity-kit'
 
export default function Home() {
  return <ProfileCard addressOrName="vitalik.eth" />
  // or 0x983110309620d911731ac0932219af06091b6744
}import 'ethereum-identity-kit/css'transpilePackages: ['ethereum-identity-kit'],ssr: {
  noExternal: ['ethereum-identity-kit'],
},
* import { FullWidthProfile } from 'ethereum-identity-kit'
 
export default function Home() {
  return <FullWidthProfile addressOrName="cottons.eth" />
}
* import { ProfileCard } from 'ethereum-identity-kit'
 
export default function Home() {
  return <ProfileCard addressOrName="vitalik.eth" />
}
* import { ProfileTooltip } from 'ethereum-identity-kit'
 
export default function Home() {
  return (
    <ProfileTooltip addressOrName="vitalik.eth" darkMode={true}>
      <span>Hover over me to see profile</span>
    </ProfileTooltip>
  )
}

# ethidentitykit.com llms.txt

> Ethereum Identity Kit facilitates the integration of Ethereum identity features into applications via a React component library, providing developers with tools and documentation for user profile management and on-chain transactions.

> Updated at: 22:35 05/28/25

## Components

- [followers-you-know](https://ethidentitykit.com/docs/components/followers-you-know): The Followers you know component displays a list of common followers between two Ethereum addresses or ENS names, showing their avatars and names.
- [profile-socials](https://ethidentitykit.com/docs/components/profile-socials): The Profile Socials component displays the social links of a user, including URLs and decentralized web links.
- [transaction-modal](https://ethidentitykit.com/docs/components/transaction-modal): The Transaction Modal component allows users to initiate and manage on-chain transactions. It provides a user interface for viewing transaction details, selecting chains, and managing transaction batches.
- [avatar](https://ethidentitykit.com/docs/components/avatar): The Avatar component displays an avatar image for a given Ethereum address or ENS name, with support for fallback images.
- [profile-stats](https://ethidentitykit.com/docs/components/profile-stats): The Profile Stats component displays follower and following statistics for a given Ethereum address or ENS name.
- [follower-tag](https://ethidentitykit.com/docs/components/follower-tag): The Follower Tag component displays the relationship status between a given Ethereum address and the connected user, such as whether the user follows, blocks, or mutes the address.
- [full-width-profile](https://ethidentitykit.com/docs/components/full-width-profile): The Full Width Profile component displays a comprehensive Ethereum Profile with ENS and EFP details.
- [follow-button](https://ethidentitykit.com/docs/components/follow-button): The Follow Button component allows users to manage their social connection with another user. It displays the current relationship status between the `lookupAddress` and the `connectedAddress` and provides actions to change this state.
- [transaction-provider](https://ethidentitykit.com/docs/components/transaction-provider): The Transaction Provider component supplies the necessary context for managing on-chain transactions within the application.
- [profile-card](https://ethidentitykit.com/docs/components/profile-card): The Profile Card component displays a user's ENS and EFP details.

## Functions

- [list-ops](https://ethidentitykit.com/docs/functions/list-ops): The list operations module provides utility functions for creating list operations in the EFP (Ethereum Follow Protocol) system.
- [transactions](https://ethidentitykit.com/docs/functions/transactions): The transactions module provides utility functions for handling EFP (Ethereum Follow Protocol) list operations and transactions.
- [validity](https://ethidentitykit.com/docs/functions/validity): The validity module provides utility functions for validating various types of data in the application.
- [list-storage-location](https://ethidentitykit.com/docs/functions/list-storage-location): The list storage location module provides functionality to retrieve the storage location of an EFP list from the list registry contract.
- [formatters](https://ethidentitykit.com/docs/functions/formatters): The formatters module provides utility functions for formatting various types of data in the application.
- [profile](https://ethidentitykit.com/docs/functions/profile): The profile module provides utility functions for handling profile-related operations.
- [generate-slot](https://ethidentitykit.com/docs/functions/generate-slot): The generateSlot utility generates a random storage slot value using keccak256 and the current timestamp.
- [fetch-followers-you-know](https://ethidentitykit.com/docs/functions/api/fetch-followers-you-know): Fetches the list of followers that you (connected address) follow, who also follow another address.
- [fetch-follow-state](https://ethidentitykit.com/docs/functions/api/fetch-follow-state): Fetches the follow state between two addresses or a list and an address.
- [fetch-profile-efp-poaps](https://ethidentitykit.com/docs/functions/api/fetch-profile-efp-poaps): Fetches EFP [POAPs (Proof of Attendance Protocol)](https://poap.xyz).
- [fetch-eth-price](https://ethidentitykit.com/docs/functions/api/fetch-eth-price): Fetches the current ETH price in USD from the CoinGecko API.
- [fetch-profile-details](https://ethidentitykit.com/docs/functions/api/fetch-profile-details): Fetches profile details for a given Ethereum address, ENS name, or list number.
- [fetch-profile-lists](https://ethidentitykit.com/docs/functions/api/fetch-profile-lists): Fetches all lists associated with a given address or ENS name.
- [fetch-profile-stats](https://ethidentitykit.com/docs/functions/api/fetch-profile-stats): Fetches profile statistics (followers and following counts) for a given address, ENS name, or list.
- [fetch-account](https://ethidentitykit.com/docs/functions/api/fetch-account): Fetches condensed account information for a given address, ENS name, or list.
- [fetch-recommended](https://ethidentitykit.com/docs/functions/api/fetch-recommended): Fetches recommended profiles or recent activity from the EFP API, with optional pagination.
- [fetch-all-followers-you-know](https://ethidentitykit.com/docs/functions/api/fetch-all-followers-you-know): Fetches a paginated list of followers that you (connected address) follow, who also follow another address, with optional search functionality.

## Hooks

- [useFollowButton](https://ethidentitykit.com/docs/hooks/useFollowButton): The `useFollowButton` hook manages the state and actions for a follow button component.
- [useProfileDetails](https://ethidentitykit.com/docs/hooks/useProfileDetails): The `useProfileDetails` hook fetches and manages the profile details for a given Ethereum address or ENS name, including ENS data and primary list information.
- [useFollowingState](https://ethidentitykit.com/docs/hooks/useFollowingState): The `useFollowingState` hook fetches and manages the following state between a given Ethereum address or ENS name and the connected user, indicating if the user follows, blocks, or mutes the address.
- [useFollowerState](https://ethidentitykit.com/docs/hooks/useFollowerState): The `useFollowerState` hook fetches and manages the follower state between a given Ethereum address or ENS name and the connected user, indicating if the user is followed, blocked, or muted by the address.
- [useProfileStats](https://ethidentitykit.com/docs/hooks/useProfileStats): The `useProfileStats` hook fetches and manages the follower and following statistics for a given Ethereum address or ENS name.
- [useTransactions](https://ethidentitykit.com/docs/hooks/useTransactions): The `useTransactions` hook provides access to the transaction context, allowing components to manage and interact with on-chain transactions.
- [Interpreting EFP Data](https://ethidentitykit.com/docs/services/interpreting-state): Interpreting EFP Data 
- [EFP Railway Template](https://ethidentitykit.com/docs/services/efp-silo): Deploying the EFP Railway Template  
- [EFP Infrastructure](https://ethidentitykit.com/docs/services/infra): EFP Infrastructure 

## API

- [Discover](https://ethidentitykit.com/docs/api/discover): Get recently active accounts to follow.
- [Metadata](https://ethidentitykit.com/docs/api/token/metadata): Get NFT metadata for a specified token id 
- [Image](https://ethidentitykit.com/docs/api/token/image): Get NFT image for a specified token id
- [Stats](https://ethidentitykit.com/docs/api/stats): Get global EFP statistics.
- [Export State](https://ethidentitykit.com/docs/api/export-state): Get all accounts that are being followed by EFP list id, excludes blocks and mutes 
- [Recommended](https://ethidentitykit.com/docs/api/lists/recommended): Get recommended users for a user by their EFP list id.
- [Latest Followers](https://ethidentitykit.com/docs/api/lists/latestFollowers): Get the latest followers (excluding blocked and muted) of a user by their EFP list id.
- [Stats](https://ethidentitykit.com/docs/api/lists/stats): Get stats of a user by their EFP list id.
- [Details](https://ethidentitykit.com/docs/api/lists/details): Get details of a user by their EFP list id.
- [Account](https://ethidentitykit.com/docs/api/lists/account): Get account information by their EFP list id 
- [All Following Addresses](https://ethidentitykit.com/docs/api/lists/allFollowingAddresses): Get all accounts in list format, that are being followed (including blocked and muted) by a user by their EFP list id.
- [Search Followers](https://ethidentitykit.com/docs/api/lists/searchFollowers): Search for followers of a user by their EFP list id.
- [Poap Badges](https://ethidentitykit.com/docs/api/lists/badges): Get EFP POAPs of a user by their EFP list id.
- [Search Following](https://ethidentitykit.com/docs/api/lists/searchFollowing): Search for following of a user by their EFP list id.
- [All Followers](https://ethidentitykit.com/docs/api/lists/allFollowers): Get all followers (including blocked and muted) of a user by their EFP list id.
- [Tagged As](https://ethidentitykit.com/docs/api/lists/taggedAs): Get the tags that are applied to a user by their EFP list id.
- [Tags](https://ethidentitykit.com/docs/api/lists/tags): Get the tags of a user by their EFP list id.
- [Button State](https://ethidentitykit.com/docs/api/lists/buttonState): Get the following state between a given list and a given user.
- [Following](https://ethidentitykit.com/docs/api/lists/following): Get accounts being followed (excluding blocked and muted) by a user by their EFP list id.
- [All Following](https://ethidentitykit.com/docs/api/lists/allFollowing): Get all accounts being followed (including blocked and muted) by a user by their EFP list id.
- [Follower State](https://ethidentitykit.com/docs/api/lists/followerState): Get the follower state between a given list and a given user.
- [Followers](https://ethidentitykit.com/docs/api/lists/followers): Get followers (excluding blocked and muted) of a user by their EFP list id.
- [List Records](https://ethidentitykit.com/docs/api/users/listRecords): Get the list records of a user by their address or ENS name.
- [Recommended](https://ethidentitykit.com/docs/api/users/recommended): Get recommended users for a user by their address or ENS name.
- [Lists](https://ethidentitykit.com/docs/api/users/lists): Get the lists of a user by their address or ENS name.
- [Latest Followers](https://ethidentitykit.com/docs/api/users/latestFollowers): Get a user's latest followers by Address or ENS Name  
- [Notifications](https://ethidentitykit.com/docs/api/users/notifications): Get incoming actions received from other users by Address or ENS Name  
- [Stats](https://ethidentitykit.com/docs/api/users/stats): Get stats of a user by their address or ENS name.
- [Details](https://ethidentitykit.com/docs/api/users/details): Get account details, populates most of the data on a profile card  
- [Common Followers](https://ethidentitykit.com/docs/api/users/commonFollowers): Get common followers that are shared by two accounts  
- [QR Code](https://ethidentitykit.com/docs/api/users/qr): Get a QR code that links to a user's profile page.
- [Account](https://ethidentitykit.com/docs/api/users/account): Get account information by Address or ENS Name  
- [Search Followers](https://ethidentitykit.com/docs/api/users/searchFollowers): Search for followers of a user by their address or ENS name.
- [Poap Badges](https://ethidentitykit.com/docs/api/users/badges): Get EFP POAPs of a user by their address or ENS name.
- [Primary List](https://ethidentitykit.com/docs/api/users/primaryList): Get the primary list of a user by their address or ENS name.
- [Search Following](https://ethidentitykit.com/docs/api/users/searchFollowing): Search for following of a user by their address or ENS name.
- [ENS](https://ethidentitykit.com/docs/api/users/ens): Get the ENS data of a user by their address or ENS name.
- [Tagged As](https://ethidentitykit.com/docs/api/users/taggedAs): Get the tags that are applied to a user by their address or ENS name.
- [Tags](https://ethidentitykit.com/docs/api/users/tags): Get the tags of a user by their address or ENS name.
- [Following](https://ethidentitykit.com/docs/api/users/following): Get following by Address or ENS Name 
- [Follower State](https://ethidentitykit.com/docs/api/users/followerState): Get the follower state between two users.
- [Followers](https://ethidentitykit.com/docs/api/users/followers): Get followers by Address or ENS Name  
- [Introduction](https://ethidentitykit.com/docs/api/index): EFP provides an open source indexer and API for indexing and retrieving EFP data.
- [Blocked](https://ethidentitykit.com/docs/api/leaderboard/blocked): Get leaderboard of users ranked according to count of users that blocked them.
- [All](https://ethidentitykit.com/docs/api/leaderboard/all): Get addresses and ens names of all leaderboard records.
- [Ranked](https://ethidentitykit.com/docs/api/leaderboard/ranked): Get leaderboard of users ranked according to count of mutual follows.
- [Search](https://ethidentitykit.com/docs/api/leaderboard/search): Search for leaderboard addresses and ENS names by a specified search term.
- [Muted](https://ethidentitykit.com/docs/api/leaderboard/muted): Get leaderboard of users ranked according to count of users that muted them.
- [Count](https://ethidentitykit.com/docs/api/leaderboard/count): Get count of all accounts in the leaderboard.
- [Mutes](https://ethidentitykit.com/docs/api/leaderboard/mutes): Get leaderboard of users ranked according to count of users that they muted.
- [Following](https://ethidentitykit.com/docs/api/leaderboard/following): Get leaderboard of users ranked according to following counts.
- [Blocks](https://ethidentitykit.com/docs/api/leaderboard/blocks): Get leaderboard of users ranked according to count of users that they blocked.
- [Followers](https://ethidentitykit.com/docs/api/leaderboard/followers): Get leaderboard of users ranked according to follower counts.
- [Details by Slot](https://ethidentitykit.com/docs/api/slots/details): Get list details by slot# ethidentitykit.com llms-full.txt

> Ethereum Identity Kit facilitates the integration of Ethereum identity features into applications via a React component library, providing developers with tools and documentation for user profile management and on-chain transactions.

> Updated at: 22:35 05/28/25

# useFollowButton

** The `useFollowButton` hook manages the state and actions for a follow button component. It determines the current follow state between a `lookupAddress` and a `connectedAddress`, and provides functions to handle follow, unfollow, block, and mute actions.

### Add to your project

```tsx copy
import { useFollowButton } from 'ethereum-identity-kit'

export default function FollowButtonComponent() {
  const { buttonText, buttonState, handleAction, isLoading, disableHover, setDisableHover } = useFollowButton({
    lookupAddress: '0x1234...abcd',
    connectedAddress: '0xabcd...1234',
  })

  // Create your own loading states
  if (isLoading) return <div>Loading...</div>

  return (
    <button
      className={`follow-button ${disableHover ? 'no-hover' : ''}`}
      onClick={handleAction}
      onMouseEnter={() => setDisableHover(false)}
    >
      {buttonText}
    </button>
  )
}
```

## Parameters

| Parameter          | Description                                                               | Required | Default Value |
| ------------------ | ------------------------------------------------------------------------- | -------- | ------------- |
| `lookupAddress`    | Ethereum address to manage the follow state for.                          | Yes      | -             |
| `connectedAddress` | Ethereum address of the currently connected user.                         | No       | -             |
| `selectedList`     | List number to manage the follow state for; defaults to the primary list. | No       | -             |

## Return Values

| Return Value      | Description                                                                                  |
| ----------------- | -------------------------------------------------------------------------------------------- |
| `buttonText`      | The text to display on the follow button, indicating the current or pending follow state.    |
| `buttonState`     | The current state of the button, such as 'Follow', 'Following', 'Blocked', etc.              |
| `handleAction`    | Function to handle the button click action, updating the follow state accordingly.           |
| `isLoading`       | Boolean indicating if the follow state is currently loading.                                 |
| `pendingState`    | The pending state of the follow action, if any (e.g., 'Pending Following', 'Pending Block'). |
| `disableHover`    | Boolean indicating if hover effects should be disabled. (it is disabled after a click)       |
| `setDisableHover` | Function to set the `disableHover` state.                                                    |

### Notes

- Ensure that the `lookupAddress` and `connectedAddress` are valid Ethereum addresses.
- The `handleAction` function manages the follow, unfollow, block, and mute actions based on the current state.
- The `disableHover` state can be used to control hover effects on the button during certain actions as the state is set to true every time the button is clicked.

---

# useProfileDetails

The `useProfileDetails` hook fetches and manages the profile details for a given Ethereum address or ENS name, including ENS data and primary list information.

### Add to your project

```tsx copy
import { useProfileDetails } from 'ethereum-identity-kit'

export default function ProfileComponent() {
  const { ens, address, primaryList, detailsLoading, refreshProfileDetails } = useProfileDetails({
    addressOrName: 'vitalik.eth',
  })

  if (detailsLoading) return <div>Loading...</div> // Create your own loading states

  // --- Your component code here ---
}
```

## Parameters

| Parameter               | Description                                                                      | Required | Default Value |
| ----------------------- | -------------------------------------------------------------------------------- | -------- | ------------- |
| `addressOrName`         | Ethereum Address or ENS name to fetch profile details for.                       | Yes      | -             |
| `list`                  | List number to fetch profile details for; overrides `addressOrName` if provided. | No       | -             |
| `prefetchedData`        | Prefetched profile data to use initially.                                        | No       | -             |
| `refetchPrefetchedData` | Function to refetch prefetched profile data.                                     | No       | -             |

## Return Values

| Return Value            | Description                                                      |
| ----------------------- | ---------------------------------------------------------------- |
| `ens`                   | ENS data for the profile, including name and records.            |
| `address`               | Ethereum address associated with the profile.                    |
| `primaryList`           | Primary list number associated with the profile.                 |
| `detailsLoading`        | Boolean indicating if the profile details are currently loading. |
| `refreshProfileDetails` | Function to manually refresh the profile details.                |

---

# useFollowingState

The `useFollowingState` hook fetches and manages the following state between a given Ethereum address or ENS name and the connected user, indicating if the user follows, blocks, or mutes the address.

### Add to your project

```tsx copy
import { useFollowingState } from 'ethereum-identity-kit'

export default function FollowingStateComponent() {
  const { state, isLoading } = useFollowingState({
    lookupAddressOrName: 'vitalik.eth',
    connectedAddress: '0x1234...abcd',
  })

  // Create your own loading states
  if (isLoading) return <div>Loading...</div>

  // --- Your component code here ---
}
```

## Parameters

| Parameter             | Description                                                                                | Required | Default Value |
| --------------------- | ------------------------------------------------------------------------------------------ | -------- | ------------- |
| `lookupAddressOrName` | Ethereum Address or ENS name to check the following state for.                             | Yes      | -             |
| `connectedAddress`    | Ethereum address of the currently connected user.                                          | Yes      | -             |
| `list`                | List number to check the following state for; overrides `lookupAddressOrName` if provided. | No       | -             |

## Return Values

| Return Value | Description                                                                        |
| ------------ | ---------------------------------------------------------------------------------- |
| `state`      | The following state, indicating if the user follows, blocks, or mutes the address. |
| `isLoading`  | Boolean indicating if the following state is currently loading.                    |

---

# useFollowerState

The `useFollowerState` hook fetches and manages the follower state between a given Ethereum address or ENS name and the connected user, indicating if the user is followed, blocked, or muted by the address.

### Add to your project

```tsx copy
import { useFollowerState } from 'ethereum-identity-kit'

export default function FollowerStateComponent() {
  const { followState, followerTag, isFollowerStateLoading } = useFollowerState({
    addressOrName: 'vitalik.eth',
    connectedAddress: '0x1234...abcd',
  })

  // Create your own loading states
  if (isFollowerStateLoading) return <div>Loading...</div>

  // --- Your component code here ---
}
```

## Parameters

| Parameter          | Description                                                                         | Required | Default Value |
| ------------------ | ----------------------------------------------------------------------------------- | -------- | ------------- |
| `addressOrName`    | Ethereum Address or ENS name to check the follower state for.                       | Yes      | -             |
| `connectedAddress` | Ethereum address of the currently connected user.                                   | Yes      | -             |
| `list`             | List number to check the follower state for; overrides `addressOrName` if provided. | No       | -             |

## Return Values

| Return Value             | Description                                                                               |
| ------------------------ | ----------------------------------------------------------------------------------------- |
| `followState`            | The follower state, indicating if the user is followed, blocked, or muted by the address. |
| `followerTag`            | Object containing text and className for displaying the follower state.                   |
| `isFollowerStateLoading` | Boolean indicating if the follower state is currently loading.                            |

---

# useProfileStats

The `useProfileStats` hook fetches and manages the follower and following statistics for a given Ethereum address or ENS name.

### Add to your project

```tsx copy
import { useProfileStats } from 'ethereum-identity-kit'

export default function StatsComponent() {
  const { followers, following, statsLoading, refreshProfileStats } = useProfileStats({
    addressOrName: 'vitalik.eth',
  })

  // Create your own loading states
  if (statsLoading) return <div>Loading...</div>

  // --- Your component code here ---
}
```

## Parameters

| Parameter               | Description                                                                    | Required | Default Value |
| ----------------------- | ------------------------------------------------------------------------------ | -------- | ------------- |
| `addressOrName`         | Ethereum Address or ENS name to fetch profile stats for.                       | Yes      | -             |
| `list`                  | List number to fetch profile stats for; overrides `addressOrName` if provided. | No       | -             |
| `prefetchedData`        | Prefetched stats data to use initially.                                        | No       | -             |
| `refetchPrefetchedData` | Function to refetch prefetched stats data.                                     | No       | -             |

## Return Values

| Return Value          | Description                                                    |
| --------------------- | -------------------------------------------------------------- |
| `followers`           | Number of followers for the profile.                           |
| `following`           | Number of accounts the profile is following.                   |
| `statsLoading`        | Boolean indicating if the profile stats are currently loading. |
| `refreshProfileStats` | Function to manually refresh the profile stats.                |

---

# useTransactions

The `useTransactions` hook provides access to the transaction context, allowing components to manage and interact with on-chain transactions. It offers state management and utility functions for handling transaction modals, batching, and more.

### Add to your project

```tsx copy
import { useTransactions } from 'ethereum-identity-kit'

export default function TransactionComponent() {
  const {
    txModalOpen,
    setTxModalOpen,
    pendingTxs,
    addTransactions,
    goToNextTransaction,
    resetTransactions,
    isCheckoutFinished,
  } = useTransactions()

  // Example usage
  if (txModalOpen) {
    return <div>Transaction Modal is Open</div>
  }

  return <button onClick={() => setTxModalOpen(true)}>Open Transaction Modal</button>
}
```

## Return Values

| Return Value               | Description                                                    |
| -------------------------- | -------------------------------------------------------------- |
| `txModalOpen`              | Boolean indicating if the transaction modal is open.           |
| `setTxModalOpen`           | Function to set the `txModalOpen` state.                       |
| `pendingTxs`               | Array of pending transactions.                                 |
| `addTransactions`          | Function to add new transactions (any transaction).            |
| `goToNextTransaction`      | Function to proceed to the next transaction.                   |
| `resetTransactions`        | Function to reset all transactions.                            |
| `isCheckoutFinished`       | Boolean indicating if the checkout process is finished.        |
| `selectedChainId`          | ID of the selected chain for EFP list transactions.            |
| `setSelectedChainId`       | Function to set the `selectedChainId`.                         |
| `currentTxIndex`           | Index of the current transaction being processed.              |
| `setCurrentTxIndex`        | Function to set the `currentTxIndex`.                          |
| `lists`                    | EFP lists of the connected user.                               |
| `listsLoading`             | Boolean indicating if the lists are loading.                   |
| `addListOpsTransaction`    | Function to add a list operations transaction.                 |
| `removeTransactions`       | Function to remove transactions by their IDs.                  |
| `removeListOpsTransaction` | Function to remove list operations transactions by their data. |
| `selectedList`             | Currently selected list.                                       |
| `setSelectedList`          | Function to set the `selectedList`.                            |
| `nonce`                    | Nonce for the current transaction.                             |
| `setIsCheckoutFinished`    | Function to set the `isCheckoutFinished` state.                |

### `txModalOpen`

**Description**:  
A boolean indicating whether the transaction modal is currently open.

**Example**:

```tsx
const { txModalOpen, setTxModalOpen } = useTransactions()

// Open the transaction modal
setTxModalOpen(true)
```

### `setTxModalOpen`

**Description**:  
A function to set the `txModalOpen` state, controlling the visibility of the transaction modal.

**Example**:

```tsx
setTxModalOpen(false) // Closes the transaction modal
```

### `pendingTxs`

**Description**:  
An array of pending transactions that are queued for processing.

**Example**:

```tsx
const { pendingTxs } = useTransactions()
console.log(pendingTxs) // Logs the list of pending transactions
```

### `addTransactions`

**Description**:  
A function to add new transactions to the pending transactions list. You can add any transaction in the following format.

**Example**:

```tsx
const txs = [
  {
    id: 'tx1',
    title: 'Transaction', // Title of the transaction to be displayed in the modal
    description: 'This transaction will do something', // Description of the transaction to be displayed in the modal
    address: '0x123', // Contract address
    abi: contractAbi, // ABI of the contract
    chainId: 1, // Chain ID
    functionName: 'function', // Function name
    args: [arg1, arg2], // Arguments to be passed to the function
  },
  // ...
]

addTransactions(txs)
```

### `addListOpsTransaction`

** Description**:  
A function to add a list operations to pending transactions. This is handled by the Follow Button component, however you can use it to add a list operations transaction manually.

** Example**:

```tsx

* import {
  useTransactions,
  listOpAddListRecord,
  listOpRemoveListRecord,
  listOpAddTag,
  listOpRemoveTag,
} from 'ethereum-identity-kit'

const { addListOpsTransaction } = useTransactions()

const listOps = []
listOps.push(listOpAddListRecord('0x1234...')) // Add a list record - follow
listOps.push(listOpRemoveListRecord('0x1234...')) // Remove a list record - unfollow
listOps.push(listOpAddTag('0x1234...', 'myTag')) // Add a tag
listOps.push(listOpRemoveTag('0x1234...', 'myTag')) // Remove a tag

addListOpsTransaction(listOps)
```

### `removeTransactions`

**Description**:  
A function to remove transactions by their IDs.

**Example**:

```tsx
removeTransactions(['tx1', 'tx2'])
```

### `removeListOpsTransaction`

**Description**:  
A function to remove list operations transactions by their data.

**Example**:

```tsx
import {
  useTransactions,
  listOpAddListRecord,
  listOpRemoveListRecord,
  listOpAddTag,
  listOpRemoveTag,
} from 'ethereum-identity-kit'

const { removeListOpsTransaction } = useTransactions()

const listOpsData = []
listOpsData.push(listOpAddListRecord('0x1234...').data) // Add a list record - follow
listOpsData.push(listOpRemoveListRecord('0x1234...').data) // Remove a list record - unfollow
listOpsData.push(listOpAddTag('0x1234...', 'myTag').data) // Add a tag
listOpsData.push(listOpRemoveTag('0x1234...', 'myTag').data) // Remove a tag

removeListOpsTransaction(listOpsData)
```

### `goToNextTransaction`

**Description**:  
A function to proceed to the next transaction in the queue.

**Example**:

```tsx
goToNextTransaction() // Moves to the next transaction
```

### `resetTransactions`

**Description**:  
A function to reset all transactions, optionally keeping the modal open.

**Example**:

```tsx
resetTransactions() // Resets all transactions and closes the modal
resetTransactions(true) // Resets all transactions but keeps the modal open
```

### `isCheckoutFinished`

**Description**:  
A boolean indicating if the checkout process is complete.

**Example**:

```tsx
const { isCheckoutFinished } = useTransactions()
if (isCheckoutFinished) {
  console.log('Checkout is complete')
}
```

### `selectedChainId`

**Description**:  
The ID of the selected blockchain network for transactions.

**Example**:

```tsx
const { selectedChainId, setSelectedChainId } = useTransactions()
setSelectedChainId(1) // Sets the selected chain to Ethereum Mainnet
```

### `setSelectedChainId`

**Description**:  
A function to set the `selectedChainId`.

**Example**:

```tsx
setSelectedChainId(137) // Sets the selected chain to Polygon
```

### `currentTxIndex`

**Description**:  
The index of the current transaction being processed.

**Example**:

```tsx
const { currentTxIndex } = useTransactions()
console.log(`Current transaction index: ${currentTxIndex}`)
```

### `setCurrentTxIndex`

**Description**:  
A function to set the `currentTxIndex`.

**Example**:

```tsx
setCurrentTxIndex(2) // Sets the current transaction index to 2
```

### `lists`

**Description**:  
The EFP lists associated with the connected user.

**Example**:

```tsx
const { lists } = useTransactions()
console.log(lists) // Logs the user's EFP lists
```

### `listsLoading`

**Description**:  
A boolean indicating if the lists are currently loading.

**Example**:

```tsx
const { listsLoading } = useTransactions()
if (listsLoading) {
  console.log('Lists are loading...')
}
```

### `selectedList`

**Description**:  
The currently selected list for operations.

**Example**:

```tsx
const { selectedList, setSelectedList } = useTransactions()
setSelectedList('myList')
```

### `setSelectedList`

**Description**:  
A function to set the `selectedList`.

**Example**:

```tsx
setSelectedList('newList')
```

### `nonce`

**Description**:  
The nonce for the current transaction.

**Example**:

```tsx
const { nonce } = useTransactions()
console.log(`Current nonce: ${nonce}`)
```

### `setIsCheckoutFinished`

**Description**:  
A function to set the `isCheckoutFinished` state.

**Example**:

```tsx
setIsCheckoutFinished(true) // Marks the checkout as finished
```

### `followingAddressesToFetchFresh`

**Description**:  
An array of addresses that need fresh data fetching.

**Example**:

```tsx
const { followingAddres# docs.efp.app llms.txt

> Ethereum Follow Protocol (EFP) is an onchain social graph protocol for Ethereum accounts.

> Updated at: 22:35 05/28/25

## Documentation 

- [EFP-Silo Deployment Guide](https://docs.efp.app/production/silo): Guide for deploying the EFP-Silo template on Railway with configuration instructions.
- [EFP Frequently Asked Questions](https://docs.efp.app/faq): To provide frequently asked questions about the Ethereum Follow Protocol and its functionalities.
- [EFP Logos Collection](https://docs.efp.app/design-components/logos): Downloadable EFP logos in multiple formats.
- [Design Component Colors](https://docs.efp.app/design-components/colors): To provide a reference for color specifications used in design components.
- [EFP List Roles](https://docs.efp.app/design/roles): Explains the roles associated with an EFP List in Ethereum including Owner, Manager, and User responsibilities.
- [EFP List Registry Overview](https://docs.efp.app/design/list-registry): Explains the EFP List Registry as an ERC-721 contract for minting EFP List NFTs.
- [Interpreting EFP Data](https://docs.efp.app/production/interpreting-state): This page explains how to interpret EFP data and validate list operations.
- [List Ops Structure](https://docs.efp.app/design/list-ops): Explains List Ops structure for list operations including encoding and operation codes.
- [List Storage Location](https://docs.efp.app/design/list-storage-location): This page outlines the specifications for defining list storage locations in the EFP system.
- [Translation Bounty Program](https://docs.efp.app/translationbounty): Encourage users to contribute translations for the EFP app and earn rewards.
- [EFP Glossary](https://docs.efp.app/design/glossary): Defines key terms related to the Ethereum Follow Protocol for users and developers.
- [Tagging System Overview](https://docs.efp.app/design/tags): Explains the tagging system used in EFP lists and their functions.
- [List Records Definition](https://docs.efp.app/design/list-records): Defines the structure and components of List Records in EFP, including versioning and record types.
- [EFP Deployments Overview](https://docs.efp.app/production/deployments): Listing smart contracts and their addresses for EFP deployments on various blockchain networks.
- [EFP Infrastructure Overview](https://docs.efp.app/production/infra): Overview of EFP's backend infrastructure components and setup.
- [EFP Follow Bot](https://docs.efp.app/production/follow-bot): To provide functionality for users to track Ethereum addresses and ENS names via a Telegram bot.
- [Bug Bounty Program](https://docs.efp.app/bugbounty): Encourages reporting vulnerabilities in specific smart contracts for monetary rewards.
- [EFP List Metadata Overview](https://docs.efp.app/design/list-metadata): Explains List Metadata structure for EFP, including keys and roles assigned to Managers and Users.
- [EFP Emergency Response](https://docs.efp.app/production/emergency-response): Outlines procedures for responding to bugs in EFP contracts and managing affected data.
- [Ethereum Follow Protocol Overview](https://docs.efp.app/intro): Explains the Ethereum Follow Protocol, its roles, and functionality for managing social graphs on Ethereum.
- [EFP Multisig Overview](https://docs.efp.app/production/multisig): This page provides information about the EFP multisig wallet, its addresses, signers, and contract privileges.
- [API Documentation Redirect](https://docs.efp.app/api/): Redirects users to the API documentation for the Eth Identity Kit.
- [Ethereum Follow Protocol Overview](https://docs.efp.app/): Explains the Ethereum Follow Protocol for creating and managing on-chain social graphs using NFTs.
- [Account Metadata Overview](https://docs.efp.app/design/account-metadata): Explains how to use Account Metadata for Ethereum accounts in the EFP ecosystem.

## Code Repositories

- [EFP App](https://github.com/ethereumfollowprotocol/app): Ethereum Follow Protocol Web App
- [EFP Docs](https://github.com/ethereumfollowprotocol/docs): Ethereum Follow Protocol Documentation
- [EFP API](https://github.com/ethereumfollowprotocol/api): Ethereum Follow Protocol Public API
- [EFP Services](https://github.com/ethereumfollowprotocol/services): Ethereum Follow Protocol Services
- [EFP Indexer](https://github.com/ethereumfollowprotocol/indexer): Ethereum Follow Protocol Indexer
- [EFP Notification Service](https://github.com/ethereumfollowprotocol/notification-service): EFP notifications served piping hot over websocket
- [EFP Follow-bot](https://github.com/ethereumfollowprotocol/follow-bot): A telegram bot for subscribing to EFP account activity
- [EFP Contracts](https://github.com/ethereumfollowprotocol/contracts): Core smart contracts of Ethereum Follow Protocol
- [EFP Replay](https://github.com/ethereumfollowprotocol/replay): EFP Historical Event Recovery
- [EFP Onchain](https://github.com/ethereumfollowprotocol/onchain): Tools and example scripts for recovering EFP data onchain

## Additional Links

- [EFP Creation Proposal](https://x.com/BrantlyMillegan/status/1648794925754974209): High level proposal for the creation of Ethereum Follow Protocol
- [The Path to Web3 Identity](https://mirror.xyz/brantly.eth/7nJZCqyvhbdTIfq4oSnNEjlUUyxS9sf3pTHcBNi8Te8): Outlines the "Web3 Identity Stack", the challenges of building it and what to build next# docs.efp.app llms-full.txt

> Ethereum Follow Protocol (EFP) is an onchain social graph protocol for Ethereum accounts.

> Updated at: 22:35 05/28/25

**Is EFP a social network?**

> No, EFP is just a social graph. It has no names or profiles (use [ENS](https://ens.domains/) for that), no authentication protocol (use [SIWE](https://login.xyz/)), nor posting or tweeting. It's a primitive of the Ethereum identity stack meant to be combined with others elements in that stack in third party apps. [This article](https://mirror.xyz/brantly.eth/7nJZCqyvhbdTIfq4oSnNEjlUUyxS9sf3pTHcBNi8Te8) explains the vision.

**Can I post or tweet on EFP?**

> No, EFP is just a social graph (e.g. who follows who). However, web3 social networks could use EFP as their social graph (just as they could use ENS for their usernames and profiles).

**So I followed some people on EFP, now what?**

> In the EFP app, there's an Onchain Feed (powered by [Interface](https://interface.social/)) showing the onchain activity of the people you follow, plus the Leaderboard that shows how you stack up against other EFP users. But the most important place to use EFP is in other apps that integrate it. We keep a non-exhaustive list of apps that have integrated EFP on our homepage.

**How can my app integrate EFP?**

> Any way you want; EFP is open protocol. Ideas include: using EFP to provide additional context for who an Ethereum account is (e.g. showing a user's EFP follower and following counts on their profile, showing friends of friends that follow them, etc), using followings for contacts or message filtering, recommendations, etc. [Our API](https://docs.efp.app/api/) is a convenient way to get EFP data. Message us on Discord or elsewhere to let us know you integrated EFP and we'll put your logo and link on our website.

**Is EFP centralized?**

> No. The core components of EFP are all onchain and decentralized. Our team maintains and runs an Indexer that mirrors all onchain EFP data to an offchain database for easy access and analysis for serving EFP data through our API. Our indexer is opensource, and anyone can spin up their own indexer or build their own.

**Is there an organization behind the creation and maintenance of EFP?**

> Yes, EFP is developed by the non-profit corporation Follow Protocol Foundation.

**How is EFP funded?**

> So far, it has been funded mostly by grants from the ENS DAO. We list the sources of our major grants on our homepage.

**What is the relationship of EFP to ENS?**

> EFP has a close relationship to ENS: EFP is designed to completement ENS and other elements of the Ethereum identity stack, e.g. EFP has no names or profiles, since it assumes composability with ENS; the ENS DAO has provided large grants to the development of EFP; and the creator of EFP, brantly.eth, used to be on the ENS core team and is still involved in the ENS DAO.

**Can I have more than one EFP List?**

> Yes, but it's usually not needed since you can use tags to sort different groups of people you follow in your one list. If you do have more than one List, only one can be designated as your Primary List (the list that represents your Ethereum account) at a time.

**Can I follow other identifiers besides Ethereum addresses?**

> Right now, EFP only support Ethereum addresses, but we plan to support other identifiers (ENS names, NFT smart contracts, etc) in the future.

**Can I see the EFP code?**

> Yep, it's all [open source on Github](https://github.com/ethereumfollowprotocol).

**Can I reset a list? As in, reset the roles and clear all the list records.**

> If you are the Owner role of the list, then yes. This is useful if you bought an EFP List number on a secondary market, or just want to start over who you're following but keep your same list number. Here's how: 1) In the Connect Wallet menu, ensure you have selected the list you want to reset. 2) Go to My Profile in the nav bar, click the 3 dot menu next to your name, and select List Settings. 3) Click Edit Settings, then Reset List. You'll then be prompted to do two transactions.

**I'm bored.!**

> After you've set up your list on EFP, [check this out](https://hackertyper.net/).

---

Ethereum Follow Protocol (EFP) is an onchain social graph protocol for Ethereum accounts.

## EFP List NFT

Users mint an EFP List NFT to create an **EFP List**.

Minting an EFP List NFT is free (plus gas).

### Roles

Every EFP List has three roles, each of which are held by an Ethereum address.

1. **Owner:**
   - Is the owner of the EFP List NFT
   - Can transfer ownership of the EFP List NFT
   - Can edit the List Storage Location, which stores the records for that list, as well as who the Manager and User are
2. **Manager:**
   - This is set in the List Records contract, not the NFT
   - Is the manager of the EFP list records and metadata
   - Can transfer the Manager role to another address
   - Can set or update the user
   - Can add/remove list records and add/remove tags
   - Can add metadata key/value to the list
3. **User:**
   - This is set in the List Records contract, not the NFT
   - The Ethereum address for whom the list is intended; the Ethereum address that is following the Ethereum addresses in the EFP List.

Typically, all three roles (Owner, Manager, User) are the same Ethereum address, but they can be different.

---

## List Storage Location

Your EFP List NFT specifies a **List Storage Location** where the **List Records** are stored, which can be one of the following:

- Ethereum L1 smart contract
- Ethereum L2 smart contract
- CCIP-read pointers for off-chain storage (future)

The List Storage Location itself (the smart contract or off-chain system) must specify a Manager role, an Ethereum account that is able to edit the List Records. Typically, the Manager will be the same Ethereum account as the Owner and User roles of the EFP List NFT, but they can be different.

To prevent frontrunning, a user should first claim a slot number in their chosen List Storage Location, then mint their EFP NFT and set their List Storage Location (with the chain, smart contract address, and secured slot number).

---

## List Records

An EFP List is formed from a set of **List Records**.

Each record has a record type, but only one record type is supported at launch:

- **Address Record**
  - Contains an Ethereum address, with zero or more tags.
  - These records are typically interpreted as a "follow" of the specified Ethereum address, with some exceptions explained in the Followers section below.

---

## Order of operations

While a user may interact with the EFP smart contracts in any order (no order is enforced in the smart contracts), it's recommended that to prevent frontrunning a user should first claim a slot number in their chosen List Storage Location, then next mint their EFP NFT and set their List Storage Location (with the chain, smart contract address, and secured slot number).


---

## Tags

A **Tag** is a string associated with a List Record in an EFP list.

Tags only count for an account if that account is also followed by the user, otherwise they're not counted.

List Records can have zero or more tags. A few tags are standardized with specified semantics. Users may also set custom tags.

## Standard Tags

- **no tag**

  - If a List Record has no tags, it is interpreted as a simple follow without further categorization.

- **"block"**

  - This tag means neither the user nor the blocked account should see each other’s activity in a relevant app.
  - List Records with this tag are not included in Followers count, even if the List Record has other tags.
  - If both “block” and “mute” tags are present, “block” takes precedence.

- **"mute"**
  - This tag means the user shouldn't see the muted account’s activity in a relevant app, but the muted account might still be able to see the user’s activity.
  - List Records with this tag are not included in Followers count, even if the List Record has other tags.
  - If both “block” and “mute” tags are present, “block” takes precedence.

- **"top8"**
  - This tag means the account should appear in the user's "Top 8" in UIs that support it.
  - If a user has more than eight followed accounts with the "top8" tag, then only show the eight most recent should be included in a "Top 8" displayed in a UI.

### Custom Tags

Users can use additional arbitrary custom tags. A custom tag can be any UTF-8 string with the following constraints:

- maximum length of 255 bytes
- no leading or trailing whitespace
- more constraints to be added as needed

---

## Account Metadata

EFP provides an Account Metadata contract that allows users to set EFP-related metadata specific to their Ethereum account, namely to specify a Primary List.

### Primary List

Determining if a list is a Primary List is a two step process: the Ethereum account that set it as the Primary List in Account Metadata must match the User role for the list.

Apps should first check the Primary List value for an Ethereum account, and if set, default to using that EFP List for that Ethereum account.

Only Primary Lists are counted as Followers.


---

## Social Graph

The social graph is formed from the union of all Primary Lists. The User role of each Primary List determines which Ethereum account is following the Ethereum addresses in that List.


### Followers

**Followers** is the total number of EFP Primary Lists that follow a particular account, excluding those whoe block or mute the account.

### Following

**Following** is the total number of unique Ethereum accounts followed by a list, excluding accounts tagged with “block” or “mute”.

---

## Base Colors

| Color         | Hex     |
| ------------- | ------- |
| Dark Grey     | #333333 |
| Yellow        | #FFF500 |
| Pink          | #FF79C9 |
| Follow Button | #FFE066 |
| Addition      | #A1F783 |
| Deletion      | #FF7C7C |
| Text Neutral  | #999999 |

## Theme Colors

| Theme     | Neutral | Text    | Grey    | NavItem   |
| --------- | ------- | ------- | ------- | --------- |
| Light     | #ffffff | #000000 | #E4E4E7 | #b4b4b4   |
| Dark      | #333333 | #ffffff | #71717A | #94a3b822 |
| Halloween | #000000 | #ffffff | #61616A | #94a3b822 |

---

List of **EFP Logos** in various file formats.

| Format | SVG | PNG |
| --- | --- | --- |
| Logo With Text (light) | <img src="/logo-full-dark.svg" alt="Full Logo SVG" height="100" width="200" /> <a href="/logo-full-dark.svg" download="efp-logo-full-dark"><u>**Download**</u></a> | <img src="/logo-full-dark.png" alt="Full Logo PNG" width="180" height="200" /> <a href="/logo-full-dark.png" download="efp-logo-full-dark"><u>**Download**</u></a> |
| Logo With Text (dark) | <img src="/logo-full.svg" alt="Full Logo SVG" height="100" width="200" /> <a href="/logo-full.svg" download="efp-logo-full"><u>**Download**</u></a> | <img src="/logo-full.png" alt="Full Logo PNG" width="180" height="200" /> <a href="/logo-full.png" download="efp-logo-full"><u>**Download**</u></a> |
| Logo Only | <img src="/logo.svg" alt="Logo SVG" width="120" height="120" /> <a href="/logo.svg" download="efp-logo"><u>**Download**</u></a> | <img src="/logo.png" alt="Logo PNG" width="120" height="120" /> <a href="/logo.png" download="efp-logo"><u>**Download**</u></a> |

---

EFP is for everyone, and that includes translating the app to make it more easily accessible to a wider range of users. Please consider using your expertise to help us do that!

*Before submitting a translation, please read this entire page carefully.*

## Rewards

Those who either submit a full translation or make a significant contribution to one may earn:
- Up to **$200** (paid in Ethereum L1 USDC)
- A special **EFP Translator POAP**

Whether a submitter earns one, both, or part the above rewards is determined at our discretion, based on the quality of the submission and extent of their contribution.

If you earn a reward, we'll send it to you soon after your translation has been merged to our app.

## Qualifying Languages

We now have a large number of languages, thanks to everyone who contributed!

Going forward, we will focus on languages with a significant number of speakers and/or significant number of crypto users. Check which languages we already have and only submit if you think it meets the above criteria. Feel free to email us asking us if the language would be accepted before you make the translation.

## How to Submit or Contribute

**Before submitting a full translation for a new language, check to see if we already have a translation for it.** You can check the language selector menu in the app or the [translations folder on Github](https://github.com/ethereumfollowprotocol/app/tree/main/public/locales), and you may want to check [pull requests](https://github.com/ethereumfollowprotocol/app/pulls) to see if one is pending approval.

**Only submit or contribute to translations for languages of which you are a native speaker** (or, in the case of dead or fictional languages, a fluent speaker). Don't use ChatGPT, Google Translate, or similar services. EFP uses niche, technical language, so **we need crypto-natives who can give us the correct translations**.

You can use one of two methods for submitting a translation:

### 1) Github

Make a copy of [this folder](https://github.com/ethereumfollowprotocol/app/tree/main/public/locales/en) which contains the English translation, translate all the words and phrases on the right side of the ":" in each line from English to the new language, and submit your translation as a pull request. Please kee all quotes, line breaks, and commas in place.

Be sure to include your ENS name (for Ethereum USDC) and an email address (for POAP claim link) in your pull request so that, if accepted, we can send you your rewards. If you'd like to keep that information private, feel free to email them to [translations@ethfollow.xyz](mailto:translations@ethfollow.xyz).

### 2) Email

If you don't know how to use Github, go to [this page](https://github.com/ethereumfollowprotocol/app/blob/main/public/locales/en/translations.json), copy and paste the text into an email, translate all the words and phrases on the right side of the ":" in each line from English to the new language, and email the translation to us at [translations@ethfollow.xyz](mailto:translations@ethfollow.xyz). Please kee all quotes, line breaks, and commas in place.

Be sure to include your ENS name (for Ethereum USDC) and an email address (for POAP claim link) in your pull request so that, if accepted, we can send you your rewards.

## Corrections

If you are a native speaker of a language and see an improper translation, you may submit a correction by the above mentioned methods. Your potential reward will be proportionate to your contribution.

## Ongoing expansions to translations

As we add new features to the app, we will add new text in English. If a translation doesn't exist for a particular word or phrase, the app will fallback to the English translation. So **if you see English when using another language in the app, it's likely the language's translation file needs a translation added for that word or phrase**.

If you are a native speaker of a language and see a missing translation, you may submit an update by the above mentioned methods. Your potential reward will be proportionate to your contribution.

---

A **List Op** is a structure used to encapsulate an operation performed on a List. It includes the following fields:

- `version`: A `uint8` representing the version of the List Op. This byte defines the schema of the subsequent bytes for encoding/decoding. This is used to ensure compatibility and facilitate future upgrades.
- `opcode`: A `uint8` indicating the operation code. This defines the action to be taken using the List Op.
- `data`: A `bytes` array which holds the operation-specific data. For instance, if the operation involves adding a List Record, this field would contain the encoded List Record.

The version is always `1`.

## Operation Codes

There are four operations defined at this time:

| Code    | Operation     | Data                                 |
| ------- | ------------- | ------------------------------------ |
| 0       | Reserved      | N/A                                  |
| 1       | Add record    | Encoded `ListRecord`                 |
| 2       | Remove record | Encoded `ListRecord`                 |
| 3       | Tag record    | Encoded `ListRecord` followed by tag |
| 4       | Untag record  | Encoded `ListRecord` followed by tag |
| 5 - 255 | Reserved      | N/A                                  |

## Encoding

`ListOps` are encoded as byte arrays, starting with a one-byte `version` and a one-byte `opcode`, followed by the `data` of variable length.

```
+------------------+-----------------+-------------------------------+
| version (1 byte) | opcode (1 byte) | data (variable length)        |
+------------------+-----------------+-------------------------------+
```

The encoding of a `ListOp` is designed to be flexible, accommodating various types of operations and their corresponding data structures.

| Byte(s) | Description                     |
| ------- | ------------------------------- |
| 0       | `ListOp` version (1 byte)       |
| 1       | Operation code (1 byte)         |
| 2 - N   | Encoded operation-specific data |

The `2 - N` byte range is variable and depends on the operation being performed.

### Example - Add Record

The following is an example of an encoded `ListOp` for adding a `ListRecord` of type 1 (address record) to a list:

| Byte(s) | Description                       | Value                                        |
| ------- | --------------------------------- | -------------------------------------------- |
| 0       | `ListOp` version (1 byte)         | `0x01`                                       |
| 1       | Operation code (1 byte)           | `0x01`                                       |
| 2       | `ListRecord` version (1 byte)     | `0x01`                                       |
| 3       | `ListRecord` record type (1 byte) | `0x01`                                       |
| 4 - 23  | `ListRecord` data (20 bytes)      | `0x00000000000000000000000000000000DeaDBeef` |

### Example - Remove Record

The following is an example of an encoded `ListOp` for removing a `ListRecord` of type 1 (address record) from a list:

| Byte(s) | Description                       | Value                                        |
| ------- | --------------------------------- | -------------------------------------------- |
| 0       | `ListOp` version (1 byte)         | `0x01`                                       |
| 1       | Operation code (1 byte)           | `0x02`                                       |
| 2       | `ListRecord` version (1 byte)     | `0x01`                                       |
| 3       | `ListRecord` record type (1 byte) | `0x01`                                       |
| 4 - 23  | `ListRecord` data (20 bytes)      | `0x00000000000000000000000000000000DeaDBeef` |

### Example - Tag Record

The following is an example of an encoded `ListOp` for tagging a `ListRecord` of type 1 (address record) in a list:

| Byte(s) | Description                       | Value                                        |
| ------- | --------------------------------- | -------------------------------------------- |
| 0       | `ListOp` version (1 byte)         | `0x01`                                       |
| 1       | Operation code (1 byte)           | `0x03`                                       |
| 2       | `ListRecord` version (1 byte)     | `0x01`                                       |
| 3       | `ListRecord` record type (1 byte) | `0x01`                                       |
| 4 - 23  | `ListRecord` data (20 bytes)      | `0x00000000000000000000000000000000DeaDBeef` |
| 24 - N  | Tag (variable) (UTF-8)            | `0x746167` ("tag")                           |

The tag shou# docs.ens.domains llms.txt

> The Ethereum Name Service (ENS) is a distributed, open, and extensible naming system based on the Ethereum blockchain. ENS maps human-readable names like 'alice.eth' to machine-readable identifiers such as Ethereum addresses, other cryptocurrency addresses, content hashes, metadata, and more. 

> Updated at: 22:35 05/28/25

## General

- [faq](https://docs.ens.domains/faq): Frequently Asked Questions about the Ethereum Name Service
- [dweb-intro](https://docs.ens.domains/dweb/intro): The ContentHash is a very popular component of an ENS name, first introduced in [ENSIP-7](/ensip/7).
- [ensip-index](https://docs.ens.domains/ensip/index): This page contains a summary of all the ENS Improvement Proposals (ENSIPs) that have been proposed, and their current status.
- [bugs](https://docs.ens.domains/bugs): The ENS bug bounty program rewards anyone who finds a bug in covered ENS smart contracts and ENS Labs assets.
- [terminology](https://docs.ens.domains/terminology): A technical overview of all the terminology used in the ENS documentation.
- [contracts-index](https://docs.ens.domains/contracts/index): The Ethereum Name Service Smart Contracts Overview
- [dns-tlds](https://docs.ens.domains/dns/tlds): Alongside the `.eth` Top Level Domain, the ENS Protocol also supports most of your favourite DNS Top Level Domains (such as `.com`, `.cash` or `.domains`).
- [changelog](https://docs.ens.domains/changelog): This page contains a list of changes and events that happened to the ENS protocol & ecosystem.
- [ens-discussion](https://discuss.ens.domains/) Ethereum Name Service Discussion Board

## Registry

- [registry-reverse](https://docs.ens.domains/registry/reverse): Reverse resolution in ENS - the process of mapping from an Ethereum address (eg, 0x1234.
- [registry-dns](https://docs.ens.domains/registry/dns): Registrar responsible for all DNSSEC enabled names
- [registry-eth](https://docs.ens.domains/registry/eth): The ETH Registrar is a special registrar.
- [registry-ens](https://docs.ens.domains/registry/ens): The ENS registry is the core contract that lies at the heart of ENS resolution.

## Wrapper

- [wrapper-creating-subname-registrar](https://docs.ens.domains/wrapper/creating-subname-registrar): In the [Use Cases](/wrapper/usecases#sell-or-rent-subnames) section, we talked about the ability to stand up your own "registrar" to allow other people to register/claim subnames automatically.
- [wrapper-fuses](https://docs.ens.domains/wrapper/fuses): A "fuse" is a permission or perk that can be granted/revoked on a name.
- [wrapper-expiry](https://docs.ens.domains/wrapper/expiry): In order to burn any fuses on a name, you must also set an **expiry** on it.
- [wrapper-usecases](https://docs.ens.domains/wrapper/usecases): By default, newly registered names will use the Public Resolver, which just allows the current manager/controller of the name to update any records.
- [wrapper-contracts](https://docs.ens.domains/wrapper/contracts): The Name Wrapper contract is deployed on these chains:
- [wrapper-states](https://docs.ens.domains/wrapper/states): Wrapper States
- [wrapper-overview](https://docs.ens.domains/wrapper/overview): The **Name Wrapper** is a contract for ENS that allows you to "wrap" any ENS name into a ERC-1155 NFT.

## Resolvers

- [resolvers-quickstart](https://docs.ens.domains/resolvers/quickstart): A quickstart guide to everything about resolvers.
- [resolvers-public](https://docs.ens.domains/resolvers/public): A general purpose resolver that suits most user needs.
- [resolvers-writing](https://docs.ens.domains/resolvers/writing): Every ENS name has a resolver, which is responsible for resolving information about a name.
- [resolvers-universal](https://docs.ens.domains/resolvers/universal): The Universal Resolver is a contract that handles the work of resolving a name entirely onchain, making it possible to make a single smart contract call to resolve an ENS name.
- [resolvers-interfaces](https://docs.ens.domains/resolvers/interfaces): This page is a collection of methods that a resolver MAY implement.
- [resolvers-ccip-read](https://docs.ens.domains/resolvers/ccip-read): Learn about how CCIP Read enables Offchain ENS Resolvers, how a gateway works, trust assumptions, and more.
- [resolvers-interacting](https://docs.ens.domains/resolvers/interacting): Some apps may want to allow for users to edit, update, or modify their name and its behaviour at a more advanced level.

## Dao

- [dao-governance-moderator](https://docs.ens.domains/dao/governance/moderator): When the author of a Draft Proposal asks for it to be advanced to a vote, and you agree, follow the below steps:.
- [dao-governance-process](https://docs.ens.domains/dao/governance/process): This document is a suggested process for developing and advancing ENS Governance Proposals.
- [dao-stewards](https://docs.ens.domains/dao/stewards): The DAO is governed through a democratic process in which all major matters are decided through a vote open to all holders of governance tokens.
- [dao-wg-rules](https://docs.ens.domains/dao/wg/rules): _This document represents the current state of the Working Group Rules as created by [EP0.
- [dao-index](https://docs.ens.domains/dao/index): ENS Governance
- [dao-constitution](https://docs.ens.domains/dao/constitution): The ENS constitution is a set of binding rules that determine what governance actions are legitimate for the DAO to take.
- [dao-foundation](https://docs.ens.domains/dao/foundation): Having a legal entity that represents the DAO in the "real world" is valuable for a number of reasons:.
- [dao-token](https://docs.ens.domains/dao/token): ENS Airdropped tokens to anyone who held an ENS name on _October 31st, 2021_.
- [dao-security-council](https://docs.ens.domains/dao/security-council): The ENS DAO Security Council is a 4-of-8 multi-sig with a limited mandate: to cancel malicious proposals that threaten the DAO, particularly those that would compromise the treasury.
- [dao-proposals-submit](https://docs.ens.domains/dao/proposals/submit): There are three main types of governance proposals you can make:

## Dao Proposals

- [dao-proposals-0.1](https://docs.ens.domains/dao/proposals/0.1): 'Transfer ENS treasury and contract ownership from the ENS Multisig to ENS DAO.'
- [dao-proposals-0.2](https://docs.ens.domains/dao/proposals/0.2): 'Send 213,049 ENS tokens to a new airdrop contract for users who did not receive the 2x multiplier despite owning a name that was used as a primary ENS name. As amended by EP3.'
- [dao-proposals-0.3](https://docs.ens.domains/dao/proposals/0.3): 'Amend EP2 to include funds accidentally sent back to the $ENS token contract.'
- [dao-proposals-0.4](https://docs.ens.domains/dao/proposals/0.4): 'Creates four foundational working groups and establish rules related to the creation, management, and dissolution of working groups within the ENS DAO.'
- [dao-proposals-1.1](https://docs.ens.domains/dao/proposals/1.1): 'Increases the start price for the temporary premium added when names expire from $2,000 to $100,000.'
- [dao-proposals-1.2.1](https://docs.ens.domains/dao/proposals/1.2.1): 'The removal of Brantly Millegan as Director of The ENS Foundation (the "Foundation Company.").'
- [dao-proposals-1.2.2](https://docs.ens.domains/dao/proposals/1.2.2): 'This proposal is for the election of a new Director of the ENS Foundation.'
- [dao-proposals-1.3.1](https://docs.ens.domains/dao/proposals/1.3.1): 'Budget request for Meta-Governance Working Group'
- [dao-proposals-1.3.2](https://docs.ens.domains/dao/proposals/1.3.2): 'Budget request for ENS Ecosystem Working Group'
- [dao-proposals-1.3.3](https://docs.ens.domains/dao/proposals/1.3.3): 'Budget request for Community Working Group'
- [dao-proposals-1.3.4](https://docs.ens.domains/dao/proposals/1.3.4): 'Budget request for Public Goods Working Group'
- [dao-proposals-1.4](https://docs.ens.domains/dao/proposals/1.4): 'Proposes to reimburse True Names Limited for expenses incurred on behalf of ENS and the DAO.'
- [dao-proposals-1.5](https://docs.ens.domains/dao/proposals/1.5): 'Proposes to deploy Exponential Price Oracle Contract to replace the current Linear Price Oracle Contract'
- [dao-proposals-1.6](https://docs.ens.domains/dao/proposals/1.6): 'This proposal is for the funding and establishment of a community-run OIDC Identity Provider Server for Sign-In with Ethereum, maintained by Spruce.'
- [dao-proposals-1.7](https://docs.ens.domains/dao/proposals/1.7): 'Ens the $ENS airdrop and EP2 airdrop by transferring tokens and revoking approvals.'
- [dao-proposals-1.8](https://docs.ens.domains/dao/proposals/1.8): 'Proposes to repeal the working group rules passed in EP4 and replace those rules with the working group rules specified in this proposal.'
- [dao-proposals-1.9](https://docs.ens.domains/dao/proposals/1.9): 'This is a proposal for the ENS DAO to support the Protocol Guild Pilot, a vested split contract which directs funding to 110 Ethereum core protocol contributors over one year.'
- [dao-proposals-2.1](https://docs.ens.domains/dao/proposals/2.1): 'A proposal to fund TNL for continuing development and improvement of the ENS system.'
- [dao-proposals-2.2.1](https://docs.ens.domains/dao/proposals/2.2.1): 'Budget request for Meta-Governance Working Group'
- [dao-proposals-2.2.2](https://docs.ens.domains/dao/proposals/2.2.2): 'Budget request for Ecosystem Working Group'
- [dao-proposals-2.2.3](https://docs.ens.domains/dao/proposals/2.2.3): 'Budget request for Public Goods Working Group'
- [dao-proposals-2.2.4](https://docs.ens.domains/dao/proposals/2.2.4): 'RFP for an endowment fund manager'
- [dao-proposals-2.2.5](https://docs.ens.domains/dao/proposals/2.2.5): 'Selection of an ENS endowment fund manager'
- [dao-proposals-3.1.1](https://docs.ens.domains/dao/proposals/3.1.1): 'This is a proposal to request funding for the ENS Ecosystem Working Group for Q1/Q2 2023.'
- [dao-proposals-3.1.2](https://docs.ens.domains/dao/proposals/3.1.2): 'This is a proposal to request funding for the Meta-Governance Working Group for Q1/Q2 2023.'
- [dao-proposals-3.1.3](https://docs.ens.domains/dao/proposals/3.1.3): 'This is a proposal to request funding for the Public Goods Working Group for Q1/Q2 2023.'
- [dao-proposals-3.2](https://docs.ens.domains/dao/proposals/3.2): 'This proposal executes the funding requests for the ENS DAO Working Groups for the April 2023 funding window.'
- [dao-proposals-3.3](https://docs.ens.domains/dao/proposals/3.3): 'This proposal executes a swap of 10,000 ETH into USDC, to ensure ENS DAO has enough to cover operating expenses for 18 - 24 months.'
- [dao-proposals-3.4](https://docs.ens.domains/dao/proposals/3.4): 'The first tranche of the Endowment'
- [dao-proposals-3.5](https://docs.ens.domains/dao/proposals/3.5): 'This proposal will activate the new .eth controller and reverse registrar'
- [dao-proposals-3.6](https://docs.ens.domains/dao/proposals/3.6): 'Elect a new ENS Foundation director'
- [dao-proposals-3.7](https://docs.ens.domains/dao/proposals/3.7): 'ENS Normalization Standard'
- [dao-proposals-4.1](https://docs.ens.domains/dao/proposals/4.1): 'Additional actions and strategies for the Endowment'
- [dao-proposals-4.2](https://docs.ens.domains/dao/proposals/4.2): 'Fund the Endowment (second tranche)'
- [dao-proposals-4.3](https://docs.ens.domains/dao/proposals/4.3): 'Refund Invalid .eth Names'
- [dao-proposals-4.4.1](https://docs.ens.domains/dao/proposals/4.4.1): 'This proposal requests funding for the ENS Ecosystem Working Group.'
- [dao-proposals-4.4.2](https://docs.ens.domains/dao/proposals/4.4.2): 'This proposal requests funding for the ENS Meta-Goverance Working Group.'
- [dao-proposals-4.4.3](https://docs.ens.domains/dao/proposals/4.4.3): 'This proposal requests funding for the ENS Public Goods Working Group.'
- [dao-proposals-4.5](https://docs.ens.domains/dao/proposals/4.5): 'This proposal introduces new actions and strategies to the Endowment with the aim of enhancing diversification and adapting to current market conditions. Notable additions include ETH-neutral strategy.'
- [dao-proposals-4.6](https://docs.ens.domains/dao/proposals/4.6): 'This proposal executes all three Working Group funding requests for the October 2023 funding window.'
- [dao-proposals-4.7](https://docs.ens.domains/dao/proposals/4.7): 'This proposal creates a structure for electing new service providers for the DAO'
- [dao-proposals-4.8](https://docs.ens.domains/dao/proposals/4.8): 'This proposal amends the working group rules related to Steward term duration and compensation rules.'
- [dao-proposals-4.9](https://docs.ens.domains/dao/proposals/4.9): 'This proposal aims to select service providers following the approval of EP4.7, with a budget of $3,600,000 USDC annually to support providers that can enhance the ENS system.'
- [dao-proposals-4.10](https://docs.ens.domains/dao/proposals/4.10): 'This proposal transfers ownership of the ENS root key to the ENS DAO, aiming to further decentralize governance and enhance community trust and power in managing the ENS Protocol.'
- [dao-proposals-5.1](https://docs.ens.domains/dao/proposals/5.1): "Deploy a new version of the DNSSEC oracle and DNS registrar that enables 'gasless DNSSEC' functionality."
- [dao-proposals-5.2](https://docs.ens.domains/dao/proposals/5.2): 'This EP will initiate the Streams for Service Providers as selected on EP4.9'
- [dao-proposals-5.3](https://docs.ens.domains/dao/proposals/5.3): "Decide ENS Labs' next steps in the eth.link litigation, and consider reimbursement for ENS Labs' legal expenses in this case."
- [dao-proposals-5.4.1](https://docs.ens.domains/dao/proposals/5.4.1): 'This specification is the amount requested from the DAO treasury to the Metagov Multisig to fulfill anticipated budgetary needs through September 2024.'
- [dao-proposals-5.4.2](https://docs.ens.domains/dao/proposals/5.4.2): 'This specification is the amount requested from the DAO treasury to the Public Goods  Multisig to fulfill anticipated budgetary needs through September 2024.'
- [dao-proposals-5.5](https://docs.ens.domains/dao/proposals/5.5): 'This specification is the amount requested from the DAO treasury to the Public Goods Multisig to fulfill anticipated budgetary needs through September 2024.'
- [dao-proposals-5.6](https://docs.ens.domains/dao/proposals/5.6): 'This EP authorises metagov to withdraw 30 ETH from the endowment each month for fees, and reimburses metagov for 43.54 ETH in fees already incurred.'
- [dao-proposals-5.7](https://docs.ens.domains/dao/proposals/5.7): "This EP aims to safeguard the DAO by establishing a Security Council with a two-year, time-limited veto power to counter malicious proposals, ensuring the protocol's integrity and promoting decentralized governance."
- [dao-proposals-5.8](https://docs.ens.domains/dao/proposals/5.8): "This EP aims to safeguard the DAO by establishing a Security Council with a two-year, time-limited veto power to counter malicious proposals, ensuring the protocol's integrity and promoting decentralized governance."
- [dao-proposals-5.9](https://docs.ens.domains/dao/proposals/5.9): 'This proposal seeks to use the June 2024 funding window to request Q1/Q2 funding for the ENS Meta-Governance Working Group, following the failure of the March 2024 funding request, to cover operations until the next window in September 2024.'
- [dao-proposals-5.10](https://docs.ens.domains/dao/proposals/5.10): 'This proposal confirms the 8 individuals for the Security Council, as defined in EP5.7, to protect against governance attacks by canceling malicious proposals using the SecurityCouncil smart contract.'
- [dao-proposals-5.11](https://docs.ens.domains/dao/proposals/5.11): 'This proposal funds the Meta-Governance Working Group with 374k USDC and 150k ENS to support DAO-wide operations, including Working Groups, treasury management, and governance initiatives, as specified in EP 5.9 and amended by EP 5.8.'
- [dao-proposals-5.12](https://docs.ens.domains/dao/proposals/5.12): 'This proposal aims to roll out an updated version of the Zodiac Roles Modifier module. The new version improves usability and transparency of treasury management operations. Upon approval, the Roles Modifier v2 module will be activated. Furthermore, this proposal requests authorization from the DAO to revise the permissions policy.'
- [dao-proposals-5.13](https://docs.ens.domains/dao/proposals/5.13): 'This proposal aims to establish a Security Council for the ENS DAO with the authority to veto malicious proposals, with a built-in expiration mechanism to prevent centralized control and ensure greater delegation and governance distribution over time.'
- [dao-proposals-5.14](https://docs.ens.domains/dao/proposals/5.14): 'This proposal aims to introduce new permissions for deploying Endowment funds, focusing on improved diversification and alignment with the evolving market landscape and liquidity.'
- [dao-proposals-5.15](https://docs.ens.domains/dao/proposals/5.15): 'Agora proposes adding the functionality of the ProposalBond to the ENS DAO Governor that would allow a proposer to propose with a lower threshold.'
- [dao-proposals-5.16](https://docs.ens.domains/dao/proposals/5.16): 'This executable proposal seeks to implement the reimbursement payment to ENS Labs for the legal fees incurred while pursuing litigation to protect the eth.link domain.'
- [dao-proposals-5.17.1](https://docs.ens.domains/dao/proposals/5.17.1): 'This social proposal requests $254k USDC for operations through April 2025, covering compensation, tools, and resources for governance.'
- [dao-proposals-5.17.2](https://docs.ens.domains/dao/proposals/5.17.2): 'This social proposal requests $836k USDC for ecosystem initiatives, including grants, hackathons, and partnerships.'
- [dao-proposals-5.17.3](https://docs.ens.domains/dao/proposals/5.17.3): 'This social proposal requests $236k USDC for grants, events, hackathons, and bounties supporting Web3 infrastructure'
- [dao-proposals-5.18](https://docs.ens.domains/dao/proposals/5.18): "This proposal outlines the ENS DAO's steward compensation structure for Term 6, detailing monthly USDC payments for various roles, a new $ENS token distribution tied to annual USDC compensation, and terms for DAO approval."
- [dao-proposals-5.19](https://docs.ens.domains/dao/proposals/5.19): "This proposal outlines a pilot program to distribute ENS governance tokens to eligible contributors receiving grants, bounties, or payments from the DAO, aiming to engage them in governance by issuing tokens according to a quadratic distribution model, with the program's budget to be determined by a ranked choice vote."
- [dao-proposals-5.20](https://docs.ens.domains/dao/proposals/5.20): 'This proposal introduces an Investment Policy Statement (IPS) for the ENS Endowment to clarify investment principles, roles, and performance standards, with adjustments based on community feedback to include a more conservative asset allocation and regular income transfers for sustainable growth.'
- [dao-proposals-5.21](https://docs.ens.domains/dao/proposals/5.21): This proposal seeks to compensate the blockful team with 100k USDC and 15k vested ENS tokens for their extensive efforts in identifying and mitigating a critical vulnerability in ENS DAO's governance structure, which included developing the Security Council and enhancing long-term DAO security.
- [dao-proposals-5.22](https://docs.ens.domains/dao/proposals/5.22): 'This proposal seeks to implement the revised budget stream to ENS Labs to develop, maintain and audit ENSv2.'
- [dao-proposals-5.23](https://docs.ens.domains/dao/proposals/5.23): "This proposal aims to compensate the blockful team for their work in identifying, analyzing, reporting and mitigating a severe vulnerability in ENS DAO's governance structure."
- [dao-proposals-5.24](https://docs.ens.domains/dao/proposals/5.24): 'This proposal executes all three Working Group funding requests fo# docs.siwe.xyz llms.txt

> Offering resources and guidance for integrating Sign-In with Ethereum, enhancing user control over digital identities in web applications, while promoting best practices and supporting community involvement within the Ethereum ecosystem.

> Updated at: 23:25 09/09/25

# ⭐ Deployment Guide

This guide covers deploying the SIWE OIDC Provider in production environments. Choose from multiple deployment options based on your infrastructure needs.

## Deployment Options

The SIWE OIDC Provider can be deployed in three primary modes:

1. **[Railway Template](#railway-template-deployment)** - Preconfigured and easily deployed
2. **[Cloudflare Workers](#cloudflare-workers-deployment)** - Serverless, globally distributed
3. **[Standalone Binary](#standalone-binary-deployment)** - Self-hosted with full control

## Prerequisites

### General Requirements

-   Domain name with HTTPS support
-   Basic knowledge of OIDC flows
-   Client applications that support OpenID Connect

### For Standalone Deployment

-   **Redis** database instance
-   **Docker** or container runtime (recommended)
-   **Reverse proxy** (nginx, Apache, or cloud load balancer)

### For Cloudflare Workers

-   **Cloudflare account** with Workers enabled
-   **Wrangler CLI** installed locally

## Railway Template Deployment

Railway is a platform that allows users to easily deploy and manage services and environments.  

Deploying the SIWE-OIDC template on Railway is the easiest option to deploy the service and is as simple as clicking the button below.  The template is preconfigured and only requires you to create a Railway account if you don't already have one, and enter in a Re-Own (Wallet Connect) project ID.

<a href="https://railway.com/deploy/siwe-oidc?referralCode=98Kre1" target="_blank" rel="noopener noreferrer"><img src="https://railway.com/button.svg" alt="Deploy on Railway" /></a>


## Cloudflare Workers Deployment

Cloudflare Workers provide a serverless, globally distributed deployment option.

### 1. Setup Repository

```bash
# Clone the SIWE OIDC repository
git clone https://github.com/signinwithethereum/siwe-oidc
cd siwe-oidc
```

### 2. Install Wrangler CLI

```bash
# Install Wrangler globally
npm install -g @cloudflare/wrangler

# Or install locally in project
npm install --save-dev @cloudflare/wrangler
```

### 3. Authenticate with Cloudflare

```bash
# Login to Cloudflare
wrangler auth

# Verify authentication
wrangler whoami
```

### 4. Create KV Namespace

KV storage is used for session and client data:

```bash
# Create production KV namespace
wrangler kv:namespace create "SIWE_OIDC_KV"

# Create preview KV namespace for staging
wrangler kv:namespace create "SIWE_OIDC_KV" --preview
```

### 5. Configure wrangler.toml

Update `wrangler.toml` with your account details:

```toml
name = "siwe-oidc-provider"
type = "webpack"
account_id = "your-account-id"
workers_dev = true
route = ""
zone_id = ""

[build]
command = "npm run build"

[build.upload]
format = "service-worker"

[[kv_namespaces]]
binding = "SIWE_OIDC_KV"
id = "your-kv-namespace-id"
preview_id = "your-preview-kv-namespace-id"

[vars]
SIWEOIDC_BASE_URL = "https://your-worker.your-subdomain.workers.dev"
```

### 6. Deploy to Cloudflare

```bash
# Deploy to production
wrangler publish

# Deploy to preview environment
wrangler publish --env preview
```

### 7. Configure Custom Domain (Optional)

```bash
# Add custom domain
wrangler route add "oidc.yourdomain.com/*" your-zone-id
```

## Standalone Binary Deployment

For self-hosted environments, deploy as a standalone service with Redis.

### 1. Using Docker (Recommended)

#### Quick Start

```bash
# Run with docker-compose (includes Redis)
curl -O https://raw.githubusercontent.com/spruceid/siwe-oidc/main/docker-compose.yml
docker-compose up -d
```

#### Manual Docker Deployment

```bash
# Start Redis container
docker run -d --name redis \
  -p 6379:6379 \
  redis:7-alpine

# Run SIWE OIDC Provider
docker run -d --name siwe-oidc \
  -p 8000:8000 \
  -e SIWEOIDC_ADDRESS="0.0.0.0" \
  -e SIWEOIDC_PORT="8000" \
  -e SIWEOIDC_REDIS_URL="redis://redis:6379" \
  -e SIWEOIDC_BASE_URL="https://oidc.yourdomain.com" \
  --link redis \
  ghcr.io/spruceid/siwe_oidc:latest
```

### 2. Using Docker Compose

Create `docker-compose.yml`:

```yaml
version: '3.8'

services:
    redis:
        image: redis:7-alpine
        restart: unless-stopped
        volumes:
            - redis_data:/data
        healthcheck:
            test: ['CMD', 'redis-cli', 'ping']
            interval: 10s
            timeout: 5s
            retries: 3

    siwe-oidc:
        image: ghcr.io/spruceid/siwe_oidc:latest
        restart: unless-stopped
        ports:
            - '8000:8000'
        environment:
            - SIWEOIDC_ADDRESS=0.0.0.0
            - SIWEOIDC_PORT=8000
            - SIWEOIDC_REDIS_URL=redis://redis:6379
            - SIWEOIDC_BASE_URL=https://oidc.yourdomain.com
            - SIWEOIDC_RSA_PEM=${SIWEOIDC_RSA_PEM:-}
        depends_on:
            - redis
        healthcheck:
            test:
                [
                    'CMD',
                    'curl',
                    '-f',
                    'http://localhost:8000/.well-known/openid-configuration',
                ]
            interval: 30s
            timeout: 10s
            retries: 3

volumes:
    redis_data:
```

Deploy with:

```bash
docker-compose up -d
```

### 3. Binary Installation

For direct binary installation:

```bash
# Download latest release
wget https://github.com/spruceid/siwe-oidc/releases/latest/download/siwe-oidc-linux-x86_64
chmod +x siwe-oidc-linux-x86_64

# Run with environment variables
SIWEOIDC_REDIS_URL=redis://localhost:6379 \
SIWEOIDC_BASE_URL=https://oidc.yourdomain.com \
./siwe-oidc-linux-x86_64
```

## Configuration Options

### Environment Variables

| Variable             | Description                     | Default                  | Required |
| -------------------- | ------------------------------- | ------------------------ | -------- |
| `SIWEOIDC_ADDRESS`   | IP address to bind to           | `127.0.0.1`              | No       |
| `SIWEOIDC_PORT`      | Port to listen on               | `8000`                   | No       |
| `SIWEOIDC_REDIS_URL` | Redis connection URL            | `redis://localhost:6379` | Yes      |
| `SIWEOIDC_BASE_URL`  | Public-facing base URL          | None                     | Yes      |
| `SIWEOIDC_RSA_PEM`   | RSA private key for JWT signing | Auto-generated           | No       |

### Advanced Configuration

#### Custom Signing Key

Generate and use a custom RSA key for JWT signing:

```bash
# Generate RSA private key
openssl genrsa -out private.pem 2048

# Extract public key
openssl rsa -in private.pem -pubout -out public.pem

# Use in deployment
export SIWEOIDC_RSA_PEM=$(cat private.pem)
```

#### Redis Configuration

For production, configure Redis with persistence and security:

```bash
# Redis with persistence and password
docker run -d --name redis \
  -p 6379:6379 \
  -v redis_data:/data \
  -e REDIS_PASSWORD=your-secure-password \
  redis:7-alpine \
  redis-server --requirepass your-secure-password --appendonly yes
```

## Reverse Proxy Setup

### Nginx Configuration

```nginx
server {
    listen 443 ssl http2;
    server_name oidc.yourdomain.com;

    ssl_certificate /path/to/your/cert.pem;
    ssl_certificate_key /path/to/your/key.pem;

    location / {
        proxy_pass http://localhost:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        # CORS headers for OIDC
        add_header 'Access-Control-Allow-Origin' '*' always;
        add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS' always;
        add_header 'Access-Control-Allow-Headers' 'Content-Type, Authorization' always;
    }
}
```

### Apache Configuration

```apache
<VirtualHost *:443>
    ServerName oidc.yourdomain.com

    SSLEngine on
    SSLCertificateFile /path/to/your/cert.pem
    SSLCertificateKeyFile /path/to/your/key.pem

    ProxyPreserveHost On
    ProxyRequests Off
    ProxyPass / http://localhost:8000/
    ProxyPassReverse / http://localhost:8000/

    Header always set Access-Control-Allow-Origin "*"
    Header always set Access-Control-Allow-Methods "GET, POST, OPTIONS"
    Header always set Access-Control-Allow-Headers "Content-Type, Authorization"
</VirtualHost>
```

## Local Development

### Development Setup

```bash
# Clone repository
git clone https://github.com/spruceid/siwe-oidc
cd siwe-oidc

# Start development environment with Docker Compose
docker-compose -f docker-compose.dev.yml up

# Edit /etc/hosts for local testing
echo "127.0.0.1 oidc.localhost" >> /etc/hosts
```

### Testing the Deployment

```bash
# Test OIDC configuration endpoint
curl https://oidc.yourdomain.com/.well-known/openid-configuration

# Register a test client
curl -X POST https://oidc.yourdomain.com/register \
  -H 'Content-Type: application/json' \
  -d '{
    "redirect_uris": ["https://yourapp.com/callback"],
    "client_name": "Test Client",
    "token_endpoint_auth_method": "client_secret_basic"
  }'
```

## Health Monitoring

### Health Check Endpoints

-   **Status**: `GET /.well-known/openid-configuration` - Returns 200 if service is healthy
-   **Metrics**: Custom monitoring endpoints can be added via environment variables

### Monitoring Setup

```yaml
# docker-compose monitoring addition
services:
    prometheus:
        image: prom/prometheus
        ports:
            - '9090:9090'
        volumes:
            - ./prometheus.yml:/etc/prometheus/prometheus.yml

    grafana:
        image: grafana/grafana
        ports:
            - '3000:3000'
        environment:
            - GF_SECURITY_ADMIN_PASSWORD=admin
```

## Security Considerations

### Production Checklist

-   [ ] **HTTPS Only**: Ensure all traffic uses HTTPS
-   [ ] **Secure Redis**: Use authentication and encryption
-   [ ] **Custom Keys**: Generate and securely store RSA signing keys
-   [ ] **Domain Validation**: Verify redirect URI domains
-   [ ] **Rate Limiting**: Implement request rate limiting
-   [ ] **Monitoring**: Set up logging and alerting
-   [ ] **Backups**: Regular Redis data backups
-   [ ] **Updates**: Keep container images updated

### Important Notes

⚠️ **Frontend-API Domain Requirement**: The frontend application must be served from the same subdomain as the OIDC API endpoint for security reasons.

✅ **Valid**: `app.yourdomain.com` → `oidc.yourdomain.com`  
❌ **Invalid**: `yourapp.com` → `oidc.anotherdomain.com`

## Troubleshooting

### Common Issues

1. **CORS Errors**: Ensure proper CORS headers in reverse proxy
2. **Redis Connection**: Verify Redis is running and accessible
3. **Domain Issues**: Check that frontend and API share subdomain
4. **SSL Issues**: Verify certificate is valid and properly configured

### Debug Mode

Enable debug logging:

```bash
# Add debug environment variable
RUST_LOG=debug \
SIWEOIDC_REDIS_URL=redis://localhost:6379 \
./siwe-oidc
```

---

import FullWidthLink from '@site/src/components/full-width-link'

# OIDC Provider

## Rationale

Many organizations want to consolidate the Sign in with Ethereum workflow to a single identity service (Identity Provider or IdP) that could be used to access all their federated services (Relying Parties or RPs) using [OpenID Connect](https://openid.net/connect/) to forward the user's session. This reduces overhead and mitigates security risks by consolidating authentication to one protected site instead of several, especially in complex IT systems that have many services for their users to access.

## Getting Started

The OIDC Provider implementation of Sign in with Ethereum can be found here:

<FullWidthLink
	href='https://github.com/signinwithethereum/siwe-oidc'
	logo='/img/github.svg'
	text='signinwithethereum/siwe-oidc'
	themeAware={true}
/>
<br />

Currently, two runtime modes are supported: (1) a standalone executable (using
Axum and Redis) and (2) a WASM module within a Cloudflare Worker. Both are built
from the same codebase, specializing at build time. Compilation with a `cargo` target
of `wasm32` will build for Cloudflare Worker deployments.

## Demo

A demo site is available that demonstrates how the OIDC flow works in production

<FullWidthLink
	href='https://oidc-demo.siwe.xyz'
	logo='/img/logo.svg'
	text='signinwithethereum/oidc-demo'
/>
<br />
---

import FullWidthLink from '@site/src/components/full-width-link'

# 🦀 Rust

The Rust implementation of Sign in with Ethereum can be found here:

<FullWidthLink
	href='https://github.com/signinwithethereum/siwe-rs'
	logo='/img/github.svg'
	text='signinwithethereum/siwe-rs'
	themeAware={true}
/>

## Getting Started

<FullWidthLink
	href='https://crates.io/crates/siwe'
	logo='/img/cargo.png'
	text='Sign in with Ethereum on crates.io'
/>

For detailed implementation and usage instructions, refer to the GitHub repository and crates.io documentation.

---

# Library Implementations

SIWE provides official libraries in multiple programming languages, making it easy to integrate Sign in with Ethereum authentication into applications regardless of your tech stack. Each library implements the [EIP-4361](https://eips.ethereum.org/EIPS/eip-4361) specification and provides both message creation and signature verification capabilities.

## Supported Languages

### [TypeScript/JavaScript](typescript)

The original and most feature-complete SIWE implementation.

-   **Package**: `siwe` on npm
-   **Platforms**: Node.js, Browser, React Native
-   **Features**: Complete [EIP-4361](https://eips.ethereum.org/EIPS/eip-4361) support, TypeScript definitions, extensive testing
-   **Best for**: Web applications, React/Vue/Angular apps, Node.js backends

### [Rust](rust)

High-performance implementation for Rust applications.

-   **Package**: `siwe` on crates.io
-   **Platforms**: Server applications, CLI tools, embedded systems
-   **Features**: Memory-safe, fast verification, serde serialization
-   **Best for**: High-performance backends, blockchain infrastructure, CLI tools

### [Python](python)

Pythonic implementation for Python developers.

-   **Package**: `siwe` on PyPI
-   **Platforms**: Django, Flask, FastAPI applications
-   **Features**: Async/await support, dataclass integration, type hints
-   **Best for**: Django/Flask apps, data analysis tools, ML/AI applications

### [Ruby](ruby)

Ruby gem with Rails integration support.

-   **Package**: `siwe` gem on RubyGems
-   **Platforms**: Rails applications, Sinatra, standalone Ruby scripts
-   **Features**: ActiveSupport integration, Rails middleware, comprehensive docs
-   **Best for**: Ruby on Rails applications, API backends

### [Go](go)

Go implementation for Go developers.

-   **Package**: `github.com/signinwithethereum/siwe-go`
-   **Platforms**: Go web servers, microservices, CLI applications
-   **Features**: Standard library compatibility, efficient verification, minimal dependencies
-   **Best for**: Microservices, Go web applications, infrastructure tools

### [Elixir](elixir)

Functional implementation for Elixir/Phoenix applications.

-   **Package**: `siwe` on Hex
-   **Platforms**: Phoenix applications, LiveView, OTP applications
-   **Features**: GenServer integration, Phoenix plugs, fault tolerance
-   **Best for**: Phoenix web apps, real-time applications, distributed systems

## Quick Start Comparison

Here's how to get started with each library:

### JavaScript/TypeScript

```bash
npm install siwe ethers
```

```javascript
import { SiweMessage } from 'siwe'

const message = new SiweMessage({
	domain: 'example.com',
	address: '0x...',
	uri: 'https://example.com',
	version: '1',
	chainId: 1,
})
```

### Rust

```toml
[dependencies]
siwe = "0.6"
```

```rust
use siwe::Message;

let message = Message {
    domain: "example.com".parse()?,
    address: "0x...".parse()?,
    uri: "https://example.com".parse()?,
    version: siwe::Version::V1,
    chain_id: 1,
    // ...
};
```

### Python

```bash
pip install siwe
```

```python
from siwe import SiweMessage

message = SiweMessage(
    domain="example.com",
    address="0x...",
    uri="https://example.com",
    version="1",
    chain_id=1,
)
```

### Ruby

```bash
gem install siwe
```

```ruby
require 'siwe'

message = Siwe::Message.new(
  domain: 'example.com',
  address: '0x...',
  uri: 'https://example.com',
  version: '1',
  chain_id: 1
)
```

### Go

```bash
go get github.com/signinwithethereum/siwe-go
```

```go
import "github.com/signinwithethereum/siwe-go"

message := siwe.Message{
    Domain:  "example.com",
    Address: "0x...",
    URI:     "https://example.com",
    Version: "1",
    ChainID: 1,
}
```

### Elixir

```elixir
# In mix.exs
{:siwe, "~> 0.3"}
```

```elixir
message = %Siwe.Message{
  domain: "example.com",
  address: "0x...",
  uri: "https://example.com",
  version: "1",
  chain_id: 1
}
```

## Feature Comparison

| Feature                | TypeScript     | Rust       | Python        | Ruby           | Go        | Elixir  |
| ---------------------- | -------------- | ---------- | ------------- | -------------- | --------- | ------- |
| Message Creation       | ✅             | ✅         | ✅            | ✅             | ✅        | ✅      |
| Signature Verification | ✅             | ✅         | ✅            | ✅             | ✅        | ✅      |
| Nonce Generation       | ✅             | ✅         | ✅            | ✅             | ✅        | ✅      |
| EIP-191 Support        | ✅             | ✅         | ✅            | ✅             | ✅        | ✅      |
| EIP-712 Support        | ✅             | ✅         | ✅            | ✅             | ✅        | ✅      |
| EIP-1271 Support       | ✅             | ✅         | ✅            | ✅             | ✅        | ✅      |
| Async/Await            | ✅             | ✅         | ✅            | ❌             | ✅        | ✅      |
| Type Safety            | ✅             | ✅         | ✅            | ❌             | ✅        | ✅      |
| Framework Integration  | React, Express | Axum, Warp | Django, Flask | Rails, Sinatra | Gin, Echo | Phoenix |
| Browser Support        | ✅             | ❌         | ❌            | ❌             | ❌        | ❌      |

## Choosing the Right Library

### For Web Applications

-   **Frontend**: Use TypeScript/JavaScript for React, Vue, Angular, or vanilla JS
-   **Backend**: Choose based on your existing backend language and framework

### For Mobile Applications

-   **React Native**: TypeScript/JavaScript
-   **Native iOS/Android**: Use appropriate native HTTP libraries with any backend

### For Enterprise Applications

-   **Java/.NET**: Use HTTP clients to communicate with SIWE backend services
-   **Enterprise backends**: Go, Rust, or TypeScript for high performance

### For Rapid Prototyping

-   **TypeScript/JavaScript**: Fastest to get started, works everywhere
-   **Python**: Great for data-driven applications and ML integration
-   **Ruby**: Excellent for Rails developers

## Installation Guides

Each library has specific installation and setup instructions:

-   **[TypeScript/JavaScript Setup](typescript#installation)**: npm, yarn, browser CDN
-   **[Rust Setup](rust)**: Cargo dependencies and features
-   **[Python Setup](python)**: pip, conda, virtual environments
-   **[Ruby Setup](ruby)**: gem, bundler, Rails integration
-   **[Go Setup](go)**: go mod, dependency management
-   **[Elixir Setup](elixir)**: mix deps, Phoenix integration

## Migration Guides

If you need to switch between libraries or upgrade versions:

-   [TypeScript v1 to v2 Migration](typescript#migration-guide)
-   [Cross-language Migration Tips](#cross-language-migration)
-   Version Compatibility Matrix (see below)

## Cross-Language Migration

When moving between different SIWE library implementations:

### Message Format Compatibility

All librarie# FastHTML

> FastHTML is a python library which brings together Starlette, Uvicorn, HTMX, and fastcore's `FT` "FastTags" into a library for creating server-rendered hypermedia applications. The `FastHTML` class itself inherits from `Starlette`, and adds decorator-based routing with many additions, Beforeware, automatic `FT` to HTML rendering, and much more.

Things to remember when writing FastHTML apps:

- Although parts of its API are inspired by FastAPI, it is *not* compatible with FastAPI syntax and is not targeted at creating API services
- FastHTML includes support for Pico CSS and the fastlite sqlite library, although using both are optional; sqlalchemy can be used directly or via the fastsql library, and any CSS framework can be used. Support for the Surreal and css-scope-inline libraries are also included, but both are optional
- FastHTML is compatible with JS-native web components and any vanilla JS library, but not with React, Vue, or Svelte
- Use `serve()` for running uvicorn (`if __name__ == "__main__"` is not needed since it's automatic)
- When a title is needed with a response, use `Titled`; note that that already wraps children in `Container`, and already includes both the meta title as well as the H1 element.

## Docs

- [FastHTML concise guide](https://www.fastht.ml/docs/ref/concise_guide.html.md): A brief overview of idiomatic FastHTML apps
- [HTMX reference](https://raw.githubusercontent.com/bigskysoftware/htmx/master/www/content/reference.md): Brief description of all HTMX attributes, CSS classes, headers, events, extensions, js lib methods, and config options
- [Starlette quick guide](https://gist.githubusercontent.com/jph00/e91192e9bdc1640f5421ce3c904f2efb/raw/61a2774912414029edaf1a55b506f0e283b93c46/starlette-quick.md): A quick overview of some Starlette features useful to FastHTML devs.

## API

- [API List](https://www.fastht.ml/docs/apilist.txt): A succint list of all functions and methods in fasthtml.
- [MonsterUI API List](https://raw.githubusercontent.com/AnswerDotAI/MonsterUI/refs/heads/main/docs/apilist.txt): Complete API Reference for Monster UI, a component framework similar to shadcn, but for FastHTML


## Examples

- [Websockets application](https://raw.githubusercontent.com/AnswerDotAI/fasthtml/main/examples/basic_ws.py): Very brief example of using websockets with HTMX and FastHTML
- [Todo list application](https://raw.githubusercontent.com/AnswerDotAI/fasthtml/main/examples/adv_app.py): Detailed walk-thru of a complete CRUD app in FastHTML showing idiomatic use of FastHTML and HTMX patterns.

## Optional

- [Surreal](https://raw.githubusercontent.com/AnswerDotAI/surreal/main/README.md): Tiny jQuery alternative for plain Javascript with inline Locality of Behavior, providing `me` and `any` functions
- [Starlette full documentation](https://gist.githubusercontent.com/jph00/809e4a4808d4510be0e3dc9565e9cbd3/raw/9b717589ca44cedc8aaf00b2b8cacef922964c0f/starlette-sml.md): A subset of the Starlette documentation useful for FastHTML development.
- [JS App Walkthrough](https://www.fastht.ml/docs/tutorials/e2e.html.md): An end-to-end walkthrough of a complete FastHTML app, including deployment to railway.
- [FastHTML by Example](https://www.fastht.ml/docs/tutorials/by_example.html.md): A collection of 4 FastHTML apps showcasing idiomatic use of FastHTML and HTMX patterns.
- [Using Jupyter to write FastHTML](https://www.fastht.ml/docs/tutorials/jupyter_and_fasthtml.html.md): A guide to developing FastHTML apps inside Jupyter notebooks.
- [FT Components](https://www.fastht.ml/docs/explains/explaining_xt_components.html.md): Explanation of the `FT` components, which are a way to write HTML in a Pythonic way.
- [FAQ](https://www.fastht.ml/docs/explains/faq.html.md): Answers to common questions about FastHTML.
- [MiniDataAPI Spec](https://www.fastht.ml/docs/explains/minidataapi.html.md): Explanation of the MiniDataAPI specification, which allows us to use the same API for many different database engines.
- [OAuth](https://www.fastht.ml/docs/explains/oauth.html.md): Tutorial and explanation of how to use OAuth in FastHTML apps.
- [Routes](https://www.fastht.ml/docs/explains/routes.html.md): Explanation of how routes work in FastHTML.
- [WebSockets](https://www.fastht.ml/docs/explains/websockets.html.md): Explanation of websockets and how they work in FastHTML.
- [Custom Components](https://www.fastht.ml/docs/ref/defining_xt_component.md): Explanation of how to create custom components in FastHTML.
- [Handling Handlers](https://www.fastht.ml/docs/ref/handlers.html.md): Explanation of how to request and response handlers work in FastHTML as routes.
- [Live Reloading](https://www.fastht.ml/docs/ref/live_reload.html.md): Explanation of how to use live reloading for FastHTML development.	def card_3d_demo():

	    """This is a standalone isolated Python component.

	    Behavior and styling is scoped to the component."""

	    def card_3d(text, background, amt, left_align):

	        # JS and CSS can be defined inline or in a file

	        scr = ScriptX('card3d.js', amt=amt)

	        align='left' if left_align else 'right'

	        sty = StyleX('card3d.css', background=f'url({background})', align=align)

	        return Div(text, Div(), sty, scr)

	    # Design credit: https://codepen.io/markmiro/pen/wbqMPa

	    card = card_3d("Mouseover me", bgurl, amt=1.5, left_align=True)

	    return Div(card, style=cardcss)setup(
    name = "roundup",
    version = __version__,
    classifiers = [
        'Development Status :: 4 - Beta',
        'Environment :: Console',
        'Environment :: Web Environment',
        'Intended Audience :: End Users/Desktop',
        'Intended Audience :: Developers',
        'Intended Audience :: System Administrators',
        'License :: OSI Approved :: Python Software Foundation License',
        'Operating System :: MacOS :: MacOS X',
        'Operating System :: Microsoft :: Windows',
        'Operating System :: POSIX',
        'Programming Language :: Python',
        'Topic :: Communications :: Email',
        'Topic :: Office/Business',
        'Topic :: Software Development :: Bug Tracking',
    ],
    url = 'http://sourceforge.net/projects/roundup/',
    ...
)Name: roundup
Version: 0.5.2
Classifier: Development Status :: 4 - Beta
Classifier: Environment :: Console (Text Based)
            .
            .
Classifier: Topic :: Software Development :: Bug Tracking
Url: http://sourceforge.net/projects/roundup/npm install --global @crowdin/serverless-apps-cli
crowdin-serverless-apps login
crowdin-serverless-apps create my-app
crowdin-serverless-apps dev
crowdin-serverless-apps preview
crowdin-serverless-apps publish// server.mjs
import { createServer } from 'node:http';

const server = createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello World!\n');
});

// starts a simple http server locally on port 3000
server.listen(3000, '127.0.0.1', () => {
  console.log('Listening on 127.0.0.1:3000');
});

// run with `node server.mjs`@if not defined DEBUG_HELPER @ECHO OFF

:: Other scripts rely on the environment variables set in this script, so we
:: explicitly allow them to persist in the calling shell.
endlocal

set "arg=%1"
if /i "%arg:~-1%"=="?" goto help
if /i "%arg:~-4%"=="help" goto help

cd %~dp0

set JS_SUITES=default
set NATIVE_SUITES=addons js-native-api node-api
@rem CI_* variables should be kept synchronized with the ones in Makefile
set "CI_NATIVE_SUITES=%NATIVE_SUITES% benchmark"
set "CI_JS_SUITES=%JS_SUITES% pummel"
set CI_DOC=doctool
@rem Same as the test-ci target in Makefile
set "common_test_suites=%JS_SUITES% %NATIVE_SUITES%&set build_addons=1&set build_js_native_api_tests=1&set build_node_api_tests=1"

@rem Process arguments.
set config=Release
set target=Build
set target_arch=x64
set ltcg=
set target_env=
set noprojgen=
set projgen=
set clang_cl=
set ccache_path=
set nobuild=
set sign=
set nosnapshot=
set nonpm=
set nocorepack=
set cctest_args=
set test_args=
set stage_package=
set package=
set msi=
set upload=
set licensertf=
set lint_js=
set lint_js_build=
set lint_js_fix=
set lint_cpp=
set lint_md=
set lint_md_build=
set format_md=
set i18n_arg=
set download_arg=
set build_release=
set configure_flags=
set enable_vtune_arg=
set build_addons=
set dll=
set enable_static=
set build_js_native_api_tests=
set build_node_api_tests=
set test_node_inspect=
set test_check_deopts=
set v8_test_options=
set v8_build_options=
set http2_debug=
set nghttp2_debug=
set link_module=
set no_cctest=
set cctest=
set openssl_no_asm=
set no_shared_roheap=
set doc=
set extra_msbuild_args=
set compile_commands=
set cfg=
set v8windbg=
set exit_code=0

:next-arg
if "%1"=="" goto args-done
if /i "%1"=="debug"         set config=Debug&goto arg-ok
if /i "%1"=="release"       set config=Release&set ltcg=1&set cctest=1&goto arg-ok
if /i "%1"=="clean"         set target=Clean&goto arg-ok
if /i "%1"=="testclean"     set target=TestClean&goto arg-ok
if /i "%1"=="ia32"          set target_arch=x86&goto arg-ok
if /i "%1"=="x86"           set target_arch=x86&goto arg-ok
if /i "%1"=="x64"           set target_arch=x64&goto arg-ok
if /i "%1"=="arm64"         set target_arch=arm64&goto arg-ok
if /i "%1"=="vs2022"        set target_env=vs2022&goto arg-ok
if /i "%1"=="noprojgen"     set noprojgen=1&goto arg-ok
if /i "%1"=="projgen"       set projgen=1&goto arg-ok
if /i "%1"=="clang-cl"      set clang_cl=1&goto arg-ok
if /i "%1"=="ccache"        set "ccache_path=%2%"&goto arg-ok-2
if /i "%1"=="nobuild"       set nobuild=1&goto arg-ok
if /i "%1"=="nosign"        set "sign="&echo Note: vcbuild no longer signs by default. "nosign" is redundant.&goto arg-ok
if /i "%1"=="sign"          set sign=1&goto arg-ok
if /i "%1"=="nosnapshot"    set nosnapshot=1&goto arg-ok
if /i "%1"=="nonpm"         set nonpm=1&goto arg-ok
if /i "%1"=="nocorepack"    set nocorepack=1&goto arg-ok
if /i "%1"=="ltcg"          set ltcg=1&goto arg-ok
if /i "%1"=="v8windbg"      set v8windbg=1&goto arg-ok
if /i "%1"=="licensertf"    set licensertf=1&goto arg-ok
if /i "%1"=="test"          set test_args=%test_args% %common_test_suites%&set lint_cpp=1&set lint_js=1&set lint_md=1&goto arg-ok
if /i "%1"=="test-ci-native" set test_args=%test_args% %test_ci_args% -p tap --logfile test.tap %CI_NATIVE_SUITES% %CI_DOC%&set build_addons=1&set build_js_native_api_tests=1&set build_node_api_tests=1&set cctest_args=%cctest_args% --gtest_output=xml:cctest.junit.xml&goto arg-ok
if /i "%1"=="test-ci-js"    set test_args=%test_args% %test_ci_args% -p tap --logfile test.tap %CI_JS_SUITES%&set no_cctest=1&goto arg-ok
if /i "%1"=="build-addons"   set build_addons=1&goto arg-ok
if /i "%1"=="build-js-native-api-tests"   set build_js_native_api_tests=1&goto arg-ok
if /i "%1"=="build-node-api-tests"   set build_node_api_tests=1&goto arg-ok
if /i "%1"=="test-addons"   set test_args=%test_args% addons&set build_addons=1&goto arg-ok
if /i "%1"=="test-doc"      set test_args=%test_args% %CI_DOC%&set doc=1&&set lint_js=1&set lint_md=1&goto arg-ok
if /i "%1"=="test-js-native-api"   set test_args=%test_args% js-native-api&set build_js_native_api_tests=1&goto arg-ok
if /i "%1"=="test-node-api"   set test_args=%test_args% node-api&set build_node_api_tests=1&goto arg-ok
if /i "%1"=="test-tick-processor" set test_args=%test_args% tick-processor&goto arg-ok
if /i "%1"=="test-internet" set test_args=%test_args% internet&goto arg-ok
if /i "%1"=="test-known-issues" set test_args=%test_args% known_issues&goto arg-ok
if /i "%1"=="test-all"      set test_args=%test_args% gc internet pummel %common_test_suites%&set lint_cpp=1&set lint_js=1&goto arg-ok
if /i "%1"=="test-node-inspect" set test_node_inspect=1&goto arg-ok
if /i "%1"=="test-check-deopts" set test_check_deopts=1&goto arg-ok
if /i "%1"=="test-npm"      set test_npm=1&goto arg-ok
if /i "%1"=="test-v8"       set test_v8=1&set custom_v8_test=1&goto arg-ok
if /i "%1"=="test-v8-intl"  set test_v8_intl=1&set custom_v8_test=1&goto arg-ok
if /i "%1"=="test-v8-benchmarks" set test_v8_benchmarks=1&set custom_v8_test=1&goto arg-ok
if /i "%1"=="test-v8-all"       set test_v8=1&set test_v8_intl=1&set test_v8_benchmarks=1&set custom_v8_test=1&goto arg-ok
if /i "%1"=="lint-cpp"      set lint_cpp=1&goto arg-ok
if /i "%1"=="lint-js"       set lint_js=1&goto arg-ok
if /i "%1"=="lint-js-build" set lint_js_build=1&goto arg-ok
if /i "%1"=="lint-js-fix"   set lint_js_fix=1&goto arg-ok
if /i "%1"=="jslint"        set lint_js=1&echo Please use lint-js instead of jslint&goto arg-ok
if /i "%1"=="lint-md"       set lint_md=1&goto arg-ok
if /i "%1"=="lint"          set lint_cpp=1&set lint_js=1&set lint_md=1&goto arg-ok
if /i "%1"=="lint-ci"       set lint_cpp=1&set lint_js_ci=1&goto arg-ok
if /i "%1"=="format-md"     set format_md=1&goto arg-ok
if /i "%1"=="package"       set package=1&goto arg-ok
if /i "%1"=="msi"           set msi=1&set licensertf=1&set download_arg="--download=all"&set i18n_arg=full-icu&goto arg-ok
if /i "%1"=="build-release" set build_release=1&set sign=1&goto arg-ok
if /i "%1"=="upload"        set upload=1&goto arg-ok
if /i "%1"=="small-icu"     set i18n_arg=%1&goto arg-ok
if /i "%1"=="full-icu"      set i18n_arg=%1&goto arg-ok
if /i "%1"=="intl-none"     set i18n_arg=none&goto arg-ok
if /i "%1"=="without-intl"  set i18n_arg=none&goto arg-ok
if /i "%1"=="download-all"  set download_arg="--download=all"&goto arg-ok
if /i "%1"=="ignore-flaky"  set test_args=%test_args% --flaky-tests=dontcare&goto arg-ok
if /i "%1"=="dll"           set dll=1&goto arg-ok
if /i "%1"=="enable-vtune" set enable_vtune_arg=1&goto arg-ok
if /i "%1"=="static"           set enable_static=1&goto arg-ok
if /i "%1"=="no-NODE-OPTIONS"        set no_NODE_OPTIONS=1&goto arg-ok
if /i "%1"=="debug-nghttp2" set debug_nghttp2=1&goto arg-ok
if /i "%1"=="link-module"   set "link_module= --link-module=%2%link_module%"&goto arg-ok-2
if /i "%1"=="no-cctest"     set no_cctest=1&goto arg-ok
if /i "%1"=="cctest"        set cctest=1&goto arg-ok
if /i "%1"=="openssl-no-asm"   set openssl_no_asm=1&goto arg-ok
if /i "%1"=="no-shared-roheap" set no_shared_roheap=1&goto arg-ok
if /i "%1"=="doc"           set doc=1&goto arg-ok
if /i "%1"=="binlog"        set extra_msbuild_args=/binaryLogger:out\%config%\node.binlog&goto arg-ok
if /i "%1"=="compile-commands" set compile_commands=1&goto arg-ok
if /i "%1"=="cfg"           set cfg=1&goto arg-ok

echo Error: invalid command line option `%1`.
exit /b 1

:arg-ok-2
shift
:arg-ok
shift
goto next-arg

:args-done

if defined build_release (
  set config=Release
  set package=1
  set msi=1
  set licensertf=1
  set download_arg="--download=all"
  set i18n_arg=full-icu
  set projgen=1
  set cctest=1
  set ltcg=1
)

if defined msi     set stage_package=1
if defined package set stage_package=1

:: assign path to node_exe
set "node_exe=%config%\node.exe"
set "node_gyp_exe="%node_exe%" deps\npm\node_modules\node-gyp\bin\node-gyp"
set "npm_exe="%node_exe%" deps\npm\bin\npm-cli.js"
if "%target_env%"=="vs2022" set "node_gyp_exe=%node_gyp_exe% --msvs_version=2022"

:: skip building if the only argument received was lint
if "%*"=="lint" if exist "%node_exe%" goto lint-cpp

:: skip building if the only argument received was format-md
if "%*"=="format-md" if exist "%node_exe%" goto format-md

if "%config%"=="Debug"      set configure_flags=%configure_flags% --debug
if defined nosnapshot       set configure_flags=%configure_flags% --without-snapshot
if defined nonpm            set configure_flags=%configure_flags% --without-npm
if defined nocorepack       set configure_flags=%configure_flags% --without-corepack
if defined ltcg             set configure_flags=%configure_flags% --with-ltcg
if defined release_urlbase  set configure_flags=%configure_flags% --release-urlbase=%release_urlbase%
if defined download_arg     set configure_flags=%configure_flags% %download_arg%
if defined enable_vtune_arg set configure_flags=%configure_flags% --enable-vtune-profiling
if defined dll              set configure_flags=%configure_flags% --shared
if defined enable_static    set configure_flags=%configure_flags% --enable-static
if defined no_NODE_OPTIONS  set configure_flags=%configure_flags% --without-node-options
if defined link_module      set configure_flags=%configure_flags% %link_module%
if defined i18n_arg         set configure_flags=%configure_flags% --with-intl=%i18n_arg%
if defined config_flags     set configure_flags=%configure_flags% %config_flags%
if defined target_arch      set configure_flags=%configure_flags% --dest-cpu=%target_arch%
if defined debug_nghttp2    set configure_flags=%configure_flags% --debug-nghttp2
if defined openssl_no_asm   set configure_flags=%configure_flags% --openssl-no-asm
if defined no_shared_roheap set configure_flags=%configure_flags% --disable-shared-readonly-heap
if defined DEBUG_HELPER     set configure_flags=%configure_flags% --verbose
if defined ccache_path      set configure_flags=%configure_flags% --use-ccache-win
if defined compile_commands set configure_flags=%configure_flags% -C
if defined cfg              set configure_flags=%configure_flags% --control-flow-guard
if defined v8windbg         set configure_flags=%configure_flags% --enable-v8windbg

if "%target_arch%"=="x86" if "%PROCESSOR_ARCHITECTURE%"=="AMD64" set configure_flags=%configure_flags% --no-cross-compiling

if not exist "%~dp0deps\icu" goto no-depsicu
if "%target%"=="Clean" echo deleting %~dp0deps\icu
if "%target%"=="Clean" rmdir /S /Q %~dp0deps\icu
:no-depsicu

if "%target%"=="TestClean" (
  echo deleting test/.tmp*
  if exist "test\.tmp*" for /f %%i in ('dir /a:d /s /b test\.tmp*') do rmdir /S /Q "%%i"
  goto exit
)


call tools\msvs\find_python.cmd
if errorlevel 1 goto :exit

REM NASM is only needed on IA32 and x86_64.
if not defined openssl_no_asm if "%target_arch%" NEQ "arm64" call tools\msvs\find_nasm.cmd
if errorlevel 1 echo Could not find NASM, install it or build with openssl-no-asm. See BUILDING.md.

call :getnodeversion || exit /b 1

if defined TAG set configure_flags=%configure_flags% --tag=%TAG%

if not "%target%"=="Clean" goto skip-clean
rmdir /Q /S "%~dp0%config%\%TARGET_NAME%" > nul 2> nul
:skip-clean

if defined noprojgen if defined nobuild goto :after-build

@rem Set environment for msbuild

set msvs_host_arch=x86
if _%PROCESSOR_ARCHITECTURE%_==_AMD64_ set msvs_host_arch=amd64
if _%PROCESSOR_ARCHITEW6432%_==_AMD64_ set msvs_host_arch=amd64
if _%PROCESSOR_ARCHITECTURE%_==_ARM64_ set msvs_host_arch=arm64
@rem usually vcvarsall takes an argument: host + '_' + target
set vcvarsall_arg=%msvs_host_arch%_%target_arch%
@rem unless both the host and the target are the same
if %target_arch%==x64 if %msvs_host_arch%==amd64 set vcvarsall_arg=amd64
if %target_arch%==%msvs_host_arch% set vcvarsall_arg=%target_arch%

@rem Look for Visual Studio 2022
:vs-set-2022
if defined target_env if "%target_env%" NEQ "vs2022" goto msbuild-not-found
echo Looking for Visual Studio 2022
@rem VCINSTALLDIR may be set if run from a VS Command Prompt and needs to be
@rem cleared first as vswhere_usability_wrapper.cmd doesn't when it fails to
@rem detect the version searched for
if not defined target_env set "VCINSTALLDIR="
call tools\msvs\vswhere_usability_wrapper.cmd "[17.6,18.0)" %target_arch% "prerelease" %clang_cl%
if "_%VCINSTALLDIR%_" == "__" goto msbuild-not-found
@rem check if VS2022 is already setup, and for the requested arch
if "_%VisualStudioVersion%_" == "_17.0_" if "_%VSCMD_ARG_TGT_ARCH%_"=="_%target_arch%_" goto found_vs2022
@rem need to clear VSINSTALLDIR for vcvarsall to work as expected
set "VSINSTALLDIR="
@rem prevent VsDevCmd.bat from changing the current working directory
set "VSCMD_START_DIR=%CD%"
set vcvars_call="%VCINSTALLDIR%\Auxiliary\Build\vcvarsall.bat" %vcvarsall_arg%
echo calling: %vcvars_call%
call %vcvars_call%
if errorlevel 1 goto msbuild-not-found
if defined DEBUG_HELPER @ECHO ON
:found_vs2022
echo Found MSVS version %VisualStudioVersion%
set GYP_MSVS_VERSION=2022
set PLATFORM_TOOLSET=v143
goto msbuild-found

:msbuild-not-found
set "clang_echo="
if defined clang_cl set "clang_echo= or Clang compiler/LLVM toolset"
echo Failed to find a suitable Visual Studio installation%clang_echo%.
echo Try to run in a "Developer Command Prompt" or consult
echo https://github.com/nodejs/node/blob/HEAD/BUILDING.md#windows
goto exit

:msbuild-found

@rem Visual Studio v17.10 has a bug that causes the build to fail.
@rem Check if the version is v17.10 and exit if it is.
echo %VSCMD_VER% | findstr /b /c:"17.10" >nul
if %errorlevel% neq 1  (
  echo Node.js doesn't compile with Visual Studio 17.10 Please use a different version.
  goto exit
)

@rem check if the clang-cl build is requested
if not defined clang_cl goto clang-skip
@rem x64 is hard coded as it is used for both cross and native compilation.
set "clang_path=%VCINSTALLDIR%\Tools\Llvm\x64\bin\clang.exe"
for /F "tokens=3" %%i in ('"%clang_path%" --version') do (
    set clang_version=%%i
    goto clang-found
)

:clang-not-found
echo Failed to find Clang compiler in %clang_path%.
goto exit

:clang-found
echo Found Clang version %clang_version%
set configure_flags=%configure_flags% --clang-cl=%clang_version%

:clang-skip

set project_generated=
:project-gen
@rem Skip project generation if requested.
if defined noprojgen goto msbuild
if defined projgen goto run-configure
if not exist node.sln goto run-configure
if not exist .gyp_configure_stamp goto run-configure
echo %configure_flags% > .tmp_gyp_configure_stamp
where /R . /T *.gyp* >> .tmp_gyp_configure_stamp
fc .gyp_configure_stamp .tmp_gyp_configure_stamp >NUL 2>&1
if errorlevel 1 goto run-configure

:skip-configure
del .tmp_gyp_configure_stamp 2> NUL
echo Reusing solution generated with %configure_flags%
goto msbuild

:run-configure
del .tmp_gyp_configure_stamp 2> NUL
del .gyp_configure_stamp 2> NUL
@rem Generate the VS project.
echo configure %configure_flags%
echo %configure_flags%> .used_configure_flags
call python configure %configure_flags%
if errorlevel 1 goto create-msvs-files-failed
if not exist node.sln goto create-msvs-files-failed
set project_generated=1
echo Project files generated.
echo %configure_flags% > .gyp_configure_stamp
where /R . /T *.gyp* >> .gyp_configure_stamp

:msbuild
@rem Skip build if requested.
if defined nobuild goto :after-build

@rem Build the sln with msbuild.
set "msbcpu=/m:2"
if "%NUMBER_OF_PROCESSORS%"=="1" set "msbcpu=/m:1"
set "msbplatform=Win32"
if "%target_arch%"=="x64" set "msbplatform=x64"
if "%target_arch%"=="arm64" set "msbplatform=ARM64"
if "%target%"=="Build" (
  if defined no_cctest set target=node
  if "%test_args%"=="" set target=node
  if defined cctest set target="Build"
)
if "%target%"=="node" if exist "%config%\cctest.exe" del "%config%\cctest.exe"
if "%target%"=="node" if exist "%config%\embedtest.exe" del "%config%\embedtest.exe"
if defined msbuild_args set "extra_msbuild_args=%extra_msbuild_args% %msbuild_args%"
if defined ccache_path set "extra_msbuild_args=%extra_msbuild_args% /p:TrackFileAccess=false /p:CLToolPath=%ccache_path% /p:ForceImportAfterCppProps=%CD%\tools\msvs\props_4_ccache.props"
@rem Setup env variables to use multiprocessor build
set UseMultiToolTask=True
set EnforceProcessCountAcrossBuilds=True
set MultiProcMaxCount=%NUMBER_OF_PROCESSORS%
msbuild node.sln %msbcpu% /t:%target% /p:Configuration=%config% /p:Platform=%msbplatform% /clp:NoItemAndPropertyList;Verbosity=minimal /nologo %extra_msbuild_args%
if errorlevel 1 (
  if not defined project_generated echo Building Node with reused solution failed. To regenerate project files use "vcbuild projgen"
  exit /B 1
)
if "%target%" == "Clean" goto exit

:after-build
:: Check existence of %config% before removing it.
if exist %config% rd %config%
if errorlevel 1 echo "Old build output exists at 'out\%config%'. Please remove." & exit /B
:: Use /J because /D (symlink) requires special permissions.
if EXIST out\%config% mklink /J %config% out\%config%
if errorlevel 1 echo "Could not create junction to 'out\%config%'." & exit /B

:sign
@rem Skip signing unless the `sign` option was specified.
if not defined sign goto licensertf

call tools\sign.bat Release\node.exe
if errorlevel 1 echo Failed to sign exe, got error code %errorlevel%&goto exit

:licensertf
@rem Skip license.rtf generation if not requested.
if not defined licensertf goto stage_package

set "use_x64_node_exe=false"
if "%target_arch%"=="arm64" if "%PROCESSOR_ARCHITECTURE%"=="AMD64" set "use_x64_node_exe=true"
set "x64_node_exe=temp-vcbuild\node-x64-cross-compiling.exe"
if "%use_x64_node_exe%"=="true" (
  echo Cross-compilation to ARM64 detected. We'll use the x64 Node executable for license2rtf.
  if not exist "%x64_node_exe%" (
    echo Downloading x64 node.exe...
    if not exist "temp-vcbuild" mkdir temp-vcbuild
    powershell -c "Invoke-WebRequest -Uri 'https://nodejs.org/dist/latest/win-x64/node.exe' -OutFile '%x64_node_exe%'"
  )
  if not exist "%x64_node_exe%" (
    echo Could not find the Node executable at the given x64_node_exe path. Aborting.
    set exit_code=1
    goto exit
  )
  %x64_node_exe% tools\license2rtf.mjs < LICENSE > %config%\license.rtf
) else (
  %node_exe% tools\license2rtf.mjs < LICENSE > %config%\license.rtf
)

if errorlevel 1 echo Failed to generate license.rtf, got error code %errorlevel%&goto exit

:stage_package
if not defined stage_package goto install-doctools

echo Creating package...
cd Release
rmdir /S /Q %TARGET_NAME% > nul 2> nul
mkdir %TARGET_NAME% > nul 2> nul
mkdir %TARGET_NAME%\node_modules > nul 2>nul

copy /Y node.exe %TARGET_NAME%\ > nul
if errorlevel 1 echo Cannot copy node.exe && goto package_error
copy /Y ..\LICENSE %TARGET_NAME%\ > nul
if errorlevel 1 echo Cannot copy LICENSE && goto package_error
copy /Y ..\README.md %TARGET_NAME%\ > nul
if errorlevel 1 echo Cannot copy README.md && goto package_error
copy /Y ..\CHANGELOG.md %TARGET_NAME%\ > nul
if errorlevel 1 echo Cannot copy CHANGELOG.md && goto package_error

if not defined nonpm (
  robocopy ..\deps\npm %TARGET_NAME%\node_modules\npm /e /xd test > nul
  if errorlevel 8 echo Cannot copy npm package && goto package_error
  copy /Y ..\deps\npm\bin\npm %TARGET_NAME%\ > nul
  if errorlevel 1 echo Cannot copy npm && goto package_error
  copy /Y ..\deps\npm\bin\npm.cmd %TARGET_NAME%\ > nul
  if errorlevel 1 echo Cannot copy npm.cmd && goto package_error
  copy /Y ..\deps\npm\bin\npx %TARGET_NAME%\ > nul
  if errorlevel 1 echo Cannot copy npx && goto package_error
  copy /Y ..\deps\npm\bin\npx.cmd %TARGET_NAME%\ > nul
  if errorlevel 1 echo Cannot copy npx.cmd && goto package_error
  copy /Y ..\deps\npm\bin\npm.ps1 %TARGET_NAME%\ > nul
  if errorlevel 1 echo Cannot copy npm.ps1 && goto package_error
  copy /Y ..\deps\npm\bin\npx.ps1 %TARGET_NAME%\ > nul
  if errorlevel 1 echo Cannot copy npx.ps1 && goto package_error
)

if not defined nocorepack (
  robocopy ..\deps\corepack %TARGET_NAME%\node_modules\corepack /e /xd test > nul
  if errorlevel 8 echo Cannot copy corepack package && goto package_error
  copy /Y ..\deps\corepack\shims\nodewi
