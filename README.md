# Buffalo Sabremetrics

## Background

This repository is a home for developing and sharing analysis of NCAA hockey team strength for Frozen Four bracket predictions. This analysis has its origin in the vigintennial of Scott Cavanaugh (Wesleyan University '99)'s NCAA Men's Hockey bracket.

## Statistical Approach

### Status Quo

This analysis uses manually "scraped" NCAA Men's Hockey results from the most recent season from [uscho.com](https://www.uscho.com/), and uses the R programming language to estimate team strength in order to make predictions towards making NCAA Hockey Bracket picks. The current method uses a [Terry-Bradley](https://en.wikipedia.org/wiki/Bradley%E2%80%93Terry_model)-style model applied to goal differential--using a saturated model of team-specific dummy indicators (with sign flipped for the "away" team) and intercept representing predicted home-team goal advantage. Both ordinary least squares and ordered logistic (treating each goal differential variable of ...-2, -1, 1, 2... as categorical) are estimated. Goal differential is preferred to simple win or loss (as in the canonical Terry-Bradley method) as the differential has additional information content.

In the linear regression implementation, statistical weights are used to give quadratic weight to games later in the regular season to ensure that fit prioritizes performance that is closer to tournament time.

Note also--a "coin-flipping monkey" is also implemented towards building a bracket purely intended to trash talk members of the pool who cannot perform better than a randomly-chosen bracket.

### Planned Innovations

Coming developments will including:

1. Estimate separate offense and defense parameters for each team by separating each game vs score into two team-specific outcomes.
2. Use Poisson modeling of goals to recognize this as a "count" variable.
3. Additional functions necessary to simulate outcomes for given team pairings (as the present method only requires comparison of rank in estimated parameter).

Later methods may consider correlation between errors within each game, to represent factors like game pace.
