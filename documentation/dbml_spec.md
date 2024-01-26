// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs


Table profiles {
  profile_id integer [primary key]
  name varchar(40)
  handle varchar(25)
  image varchar [note: 'URL']
  avatar varchar [note: 'URL']
  created_at timestamp
  updated_at timestamp
  last_login timestamp

  indexes {
    profile_id
    name
    handle
    image
    avatar
  }
}

Table posts {
  post_id integer [primary key]
  body varchar(250) [note: 'Content of the post']
  profile_id integer [ref: > profiles.profile_id]
  created_at timestamp

  indexes {
    post_id
    profile_id
    created_at
  }
}

Table comments {
  comment_id integer [primary key]
  body varchar(140) [note: 'Comment content']
  post_id integer [ref: - posts.post_id]
  profile_id integer [ref: > profiles.profile_id]
  created_at timestamp

  indexes {
    profile_id
    comment_id
    post_id
    created_at
  }
}

Table likes {
  like_id integer [primary key]
  post_id integer [ref: > posts.post_id]
  comment_id integer [ref: - comments.comment_id]
  profile_id integer [ref: > profiles.profile_id]
  created_at timestamp

  indexes {
    like_id
    post_id
    comment_id
  }
}

Table follows {
  id integer [primary key]
  follower_id integer  [ref: <> profiles.profile_id]
  following_id integer  [ref: <> profiles.profile_id]
  created_at timestamp

  indexes {
    follower_id
    following_id
  }
}
