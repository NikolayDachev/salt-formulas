# Salt states for managing the network

This formula manages the network configuration on a SLE/openSUSE based host.

The interface and routing configuration logic validates Salt Master connectivity after any network changes and reverts the configuration should connectivity be lost. Ideally, this should allow a Salt highstate to return even if harmful network configuration was provided in the pillar.

Operation on minions without a Salt master is currently not supported (`salt-call --local` will work as long as any Salt master is connected).

Currently only [Wicked](https://github.com/openSUSE/wicked) is supported, however the state layout is intended to facilitate other backends in the future.

## Available states

`network`

Configures all possible aspects using either the pillar specified or the default backend (Wicked).

`network.wicked`

Configures all aspects using Wicked.

`network.wicked.interfaces`

Configures interfaces using Wicked (`/etc/sysconfig/network/ifcfg-*`).

`network.wicked.routes`

Configures routes using Wicked (`/etc/sysconfig/network/routes`).

`network.wicked.netconfig`

Configures netconfig (`/etc/sysconfig/network/config`).
