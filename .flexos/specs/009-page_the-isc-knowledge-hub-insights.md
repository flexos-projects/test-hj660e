```markdown
---
type: spec
subtype: page
title: The ISC Knowledge Hub: Insights on Internet Infrastructure
route: /blog/
layout: blog_archive
---
### Purpose
To be the home for thought leadership content, technical deep-dives, and announcements, driving long-tail SEO traffic and engaging the community. This is the "ISC Knowledge Hub (Blog)" P2 feature.

### Components
1.  **PageHeader**
    *   **Description:** A header for the blog archive.
    *   **Content:** Heading ("The ISC Knowledge Hub") and a short sentence describing the content found here.

2.  **FeaturedArticle**
    *   **Description:** A large, visually prominent section at the top to feature the most recent or a manually pinned article.
    *   **Content:** A full-width card with a large featured image, the article title, publication date, author, and an excerpt.

3.  **FilterControls**
    *   **Description:** A set of controls to allow users to filter the list of articles.
    *   **Content:** A search input field (to search titles/content) and a dropdown or list of category/tag filters (e.g., "BIND 9", "Kea", "Security", "Announcements").

4.  **ArticleGrid**
    *   **Description:** A paginated grid displaying all other articles, sorted by date descending.
    *   **Content:** A grid of article cards. Each card includes a featured image, title, excerpt, and metadata (date, author).

5.  **Pagination**
    *   **Description:** Controls to navigate between pages of articles.
    *   **Content:** "Next" and "Previous" buttons, and numbered page links.

### Data Requirements
*   **FeaturedArticle:** A single `article` object, either the latest or one marked as "featured".
*   **FilterControls:** A list of all available `categories` or `tags` for filtering.
*   **ArticleGrid:** A paginated collection of `articles`. Each article object needs: `title`, `slug` (for the URL), `featured_image`, `excerpt`, `publication_date`, `author_name`, `categories`.
*   **Pagination:** Metadata from the data query, including `total_pages`, `current_page`.

### User Interactions
*   User clicks on the featured article or any article in the grid to navigate to the full article page.
*   User types in the search field to filter articles by keyword.
*   User clicks a category filter to see only articles from that category.
*   User clicks pagination links to navigate to older/newer posts.

### States
*   **Loading:** The article grid should show a loading state (e.g., skeleton cards) when filters are changed or a new page is loaded.
*   **Empty:** If no articles match the current filter or search query, a "No articles found" message is displayed.
*   **Filtering:** The UI should clearly indicate which filters are currently active.
*   **Hover:** Article cards have a clear hover state.
```